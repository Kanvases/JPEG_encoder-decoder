# YUV2JPEG
音视频课作业，从原理上实现了把一个RGB格式的frame编码为jpeg格式再解压的过程。
### 编码器功能
- RGB2YUV
- 对UV降采样。采样质量因子`scale`可以设定。
- 对YUV三个矩阵分成8\*8 的 block（在注释里叫pixel chunk）
- 对每个block进行DCT变换
- 对DCT变换结果进行量化

编码器返回一个`jpeg_picture`类型的结果，包含YUV三个分量的DCT量化结果。

### 解码器功能：
- 对三个分量进行反量化
- 对每个block进行IDCT变换
- 将8\*8的block重新拼成YUV3个矩阵
- YUV2RGB
- 保存RGB信息为ppm格式的图片

虽然ffmpeg有现成接口，但可以从原理上理解JPEG的编码过程。
源文件中有详细的英文注释，需要配一下ffmpeg。
