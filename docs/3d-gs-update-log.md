# 3D-GS更新日志



## 性能优化

### 2023-12
#### render.py图片保存性能优化

原版保存图片函数`torchvision.utils.save_image`包含以下操作，实测性能低下：

现对以下操作标号如下，测试各语句性能：
```python
# step 1
grid = torchvision.utils.make_grid(rendering)
# step 2
ndarr = grid.mul(255).add_(0.5).clamp_(0, 255).permute(1, 2, 0).to('cpu', torch.uint8).numpy()
# step 3
im = Image.fromarray(ndarr)
# step 4
im.save(os.path.join(render_path, '{0:05d}'.format(idx) + ".png"), format=None)
```

|                    实验组别                    | 帧率/fps | 操作估计消耗时间/s |
| :--------------------------------------------: | :------: | :----------------: |
| 原版保存图片函数`torchvision.utils.save_image` |   1.20   |        0.83        |
|                   不保存图片                   |   125    |         0          |
|                仅含步骤1、2、3                 |   9.06   |       0.102        |
|                  仅含步骤1、2                  |   19.5   |       0.043        |
|                   仅含步骤1                    |   201    |         0          |

由此大致可估计四个步骤的时间开销如下：0、0.043、0.059、0.73

查询相关资料后了解到，保存图片的操作的确需要这样的时间开销，因此我们使用异步线程池的方式进行优化。
```python
# 创建线程池
saveimg_thread_pool=ThreadPoolExecutor(max_workers=20)

# 使用submit调用保存图片的函数
saveimg_thread_pool.submit(torchvision.utils.save_image, rendering, os.path.join(render_path, '{0:05d}'.format(idx) + ".png"))
saveimg_thread_pool.submit(torchvision.utils.save_image, gt, os.path.join(gts_path, '{0:05d}'.format(idx) + ".png"))
```
