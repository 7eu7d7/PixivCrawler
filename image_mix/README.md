## 如何使用

### 参数说明

```bash
usage: mix.py [-h] -l LIB_DIR -t TARGET_IMAGE [-i INPUT_DIR] [-b BLOCK_SIZE] [-width OUTPUT_WIDTH] [-height OUTPUT_HEIGHT] [-m MAX_TIMES]

optional arguments:
  -h, --help            show this help message and exit
  -l LIB_DIR, --lib_dir LIB_DIR
                        image lib directory (e.g., ./image_lib/) (default: None)
  -t TARGET_IMAGE, --target_image TARGET_IMAGE
                        target image path (e.g. ./images/44873217_p0.jpg) (default: None)
  -i INPUT_DIR, --input_dir INPUT_DIR
                        raw image directory (e.g., ./images/). NOTE: set to None if image lib is already constructed (default: None)
  -b BLOCK_SIZE, --block_size BLOCK_SIZE
                        target image are divided into blocks (default: 50)
  -width OUTPUT_WIDTH, --output_width OUTPUT_WIDTH
                        width of output image (default: 4000)
  -height OUTPUT_HEIGHT, --output_height OUTPUT_HEIGHT
                        height of output image (default: 2000)
  -m MAX_TIMES, --max_times MAX_TIMES
                        max repeating times of lib blocks (default: 1)
```

- `-l LIB_DIR, --lib_dir LIB_DIR`：<u>色块库</u>目录
- `-t TARGET_IMAGE, --target_image TARGET_IMAGE`：<u>目标图片</u>路径
- `-i INPUT_DIR, --input_dir INPUT_DIR`：<u>原始图片</u>目录
- `-b BLOCK_SIZE, --block_size BLOCK_SIZE`：目标图片分块大小 / 色块库中每个色块大小
- `-width OUTPUT_WIDTH, --output_width OUTPUT_WIDTH`：输出图片宽度
- `-height OUTPUT_HEIGHT, --output_height OUTPUT_HEIGHT`：输出图片长度
- `-m MAX_TIMES, --max_times MAX_TIMES`：色块库中每个色块的最大使用次数



### 使用流程

:warning: 首次使用需要根据<u>原始图片</u>建立<u>色块库</u>，后续使用不需要重建

- 首次使用样例

  `python mix.py -l ../image_lib/ -t ../images/44873217_p0.jpg -i ../images -b 100 -width 2000 -height 1000 -m 2`

- 后续使用样例

  不需要添加`-i INPUT_DIR, --input_dir INPUT_DIR`参数

  ``python mix.py -l ../image_lib/ -t ../images/44873217_p0.jpg -b 100 -width 2000 -height 1000 -m 2``



## 算法原理

详见`mix.py`注释

1. 将原始图片转化为色块，建立色块库
2. 对于目标图片的每个色块，在色块库中选择一个最接近的色块进行替代