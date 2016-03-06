cwebp
名称

cwebp -压缩图像文件为的WebP文件
概要

cwebp [选项] INPUT_FILE -o output_file.webp
描述

cwebp压缩使用的WebP格式的图像。输入格式可以是PNG，JPEG，TIFF的WebP或生在Y'CbCr样品。
选项

基本的选项是：

-o串

    指定输出的WebP文件的名称。如果省略，cwebp将进行压缩，但只报告统计数据。使用“ - ”作为输出名称将直接输出到“标准输出”。
- 字符串

    显式地指定输入文件。如果输入的文件与启动此选项很有用“ - ”号实例。此选项必须出现最后。任何其他选项以后将被忽略。
-h，-help

    一个简短的使用说明。
-H，-longhelp

    所有可能的选项的摘要。
-版

    打印的版本号（如major.minor.revision）并退出。
-q浮动

    指定之间RGB通道的压缩系数0和100。默认值是75。

    在有损压缩（默认）的情况下，一个小的因子产生具有较低质量的更小的文件。最好的质量是通过使用一个值达到100。

    在无损压缩（由指定的情况下-lossless选项），一个小的因子能更快的压缩速度，但产生较大的文件。最大压缩是通过使用一个值达到100。
-alpha_q INT

    指定之间阿尔法压缩的压缩系数0和 100。阿尔法无损压缩是使用的值达到100，而较低的值导致一个有损压缩。默认值是 100。
-f INT

    指定去块效应滤波器的实力，与0（无过滤）和100（最大滤波）。值为0将关闭任何过滤。较高的值将增加图像解码之后施加的滤波处理的强度。该值越高，画面将出现在更顺畅。典型值通常的范围20至50。
-PRESET串

    指定一组预先定义的参数，以适应特定类型的源材料。可能的值有：默认情况下，照片，图片， 绘图，图标，文本。

    由于-PRESET覆盖其他参数值（除-q 之一），这个选项最好先出现在参数的顺序。
-sns INT

    指定空间噪声整形的幅度。空间噪声整形（或简称为SNS）是指用于决定该图像的区域应使用相对较少的位的内置算法的一般集合，并且其中别的更好传送这些比特。可能的范围内变为 0（算法是关闭的）到100（最大效果）。默认值是 80。
-m INT

    指定要使用的压缩方法。此参数控制了编码速度和压缩文件大小和质量之间的平衡。可能值的范围从0到6。默认值为4。当使用较高的值，编码器将花费更多的时间检查额外的编码可能性，并决定质量增益。较低的值可能会导致在较大的文件大小和较低的压缩质量为代价更快的处理时间。
-jpeg_like

    改变内部参数映射，以更好地匹配JPEG压缩的预期大小。这个标志通常会产生类似大小的输出文件以它的JPEG当量（对于相同-q设置），但具有更少视觉失真。
-公吨

    如果可能的话使用多线程编码。与透明通道源使用有损压缩时，此选项才有效。
-记忆不足

    通过保存压缩后大小的四倍（典型值）减少有损编码的内存使用情况。这将使得在编码慢和输出的大小和失真略有不同。此标志仅方法3和建立有效的，并且默认是关闭的。注意，离开这个标志关闭将对比特流一些副作用：它迫使某些位流的功能，如分区（强制的号码1）。需要注意的是比特流大小的更详细的报告是由打印cwebp使用此选项时。
-af

    开启自动过滤。这个算法将花费额外的时间优化滤波强度以达到良好的平衡质量。

其他选项

更高级的选项有：

-sharpness INT

    指定过滤的锐度（如果使用的话）。范围为0（锐度）到7（最锐利）。默认值为0。
-强大

    使用强过滤（如过滤被用来感谢-f 选项）。强大的过滤功能默认是开启的。
-nostrong

    禁用强滤波（如果滤波被用来感谢-f 选项），并使用简单的过滤来代替。
-segments INT

    改变的分区数的SNS算法的分割过程中使用。段应在范围1至4。默认值为4。此选项对方法第3及以上没有影响，除非-low_memory使用。
-partition_limit INT

    通过限制由一些宏块中使用的比特数降低质量。范围为0（无降解，默认值）到100（完全降解）。有用的数值通常大约是30 - 70中度高画质图像。在VP8格式中，所谓的控制分区具有512K的一个限制，用于存储以下信息：该宏块是否被跳过，它所属的段，它是否被编码为内4×4或内16×16模式，并且最后的预测模式，以用于每个子块。对于一个非常大的图象，512k的仅留下了空间，以每16×16宏块少的比特。绝对最小是每宏块4位。跳过，段，和模式信息最多可以使用几乎所有的这些4位（虽然壳体是不大可能的），这对于非常大的图像问题。所述partition_limit因子控制的频率最比特昂贵模式（内4×4）将被使用。这是有用的情况下达到了512K限制，并显示以下信息：错误代码：6（PARTITION0_OVERFLOW：分区＃0太大，以适应512K）。如果使用 -partition_limit不足以满足512k的约束，应该以每宏块节省更多的头比特使用更少的段。见-segments选项。
-size INT

    指定目标大小（以字节为单位），以试图达到的压缩输出。压缩机将进行部分编码的几通，以获得尽可能接近这一目标。
-psnr浮动

    指定目标PSNR（单位为dB），试图达到的压缩输出。压缩机将进行部分编码的几通，以获得尽可能接近这一目标。
-pass INT

    设置的推移选项一起使用二分法期间使用的最大数量 -size或-psnr。最大值是10。
调整大小宽高

    调整源与大小的矩形宽度点¯x 高度。如果（但不是两者）的宽度或高度的参数是0，值将保持纵横比来计算。
-crop x_position y_position宽度高度

    裁剪源在坐标与左上角的矩形（x_position，y_position），大小宽点¯x 高度。这复种面积必须在源矩形中完全包含。
-s宽度高度

    指定输入文件实际上是由继ITU-R BT.601推荐生在Y'CbCr样品，在4：2：0线性格式。亮度平面大小为宽点¯x 高度。
-Map INT

    输出附加ASCII地图编码信息。可能映射值的范围是1至6。这只是为了帮助调试。
-pre INT

    指定一些预处理步骤。使用值2将触发RGBA-在质量相关的伪随机抖动> YUVA转换（仅适用于有损压缩）。
-alpha_filter串

    指定阿尔法飞机的预测滤波方法。一个 没有，快或最好，在日益复杂和缓慢秩序。默认为快。在内部，阿尔法过滤是使用四种可能的预测（无，水平，垂直梯度）进行。的最佳 模式将尝试依次在每个模式并挑选一个这使较小的大小。在快速模式将只是试图形成一个先验的猜测没有测试所有的模式。
-alpha_method INT

    指定用于阿尔法压缩算法：0或1。算法 0表示不压缩，1使用的WebP无损格式进行压缩。默认值是1。
-alpha_cleanup

    修改看不见的RGB值下的全透明区域，以帮助压缩。默认是关闭的。
-blend_alpha INT

    这个选项共混alpha通道（如果存在）用十六进制作为为0xRRGGBB指定背景颜色的来源。Alpha通道之后被重置为不透明值255。
-noalpha

    使用此选项将丢弃Alpha通道。
-lossless

    编码图像而没有任何损失。
-hint串

    指定有关输入图像类型的提示。可能的值有：照片， 图片或图形。
- 元数据串

    逗号分隔的元数据的列表中，如果存在从输入复制到输出。有效值：全部，无，EXIF，ICC，XMP。默认为无。

    请注意，每个输入格式可能不支持所有组合。
-noasm

    禁用所有组件的优化。
-v

    打印额外的信息（尤其是编码时间）。
-print_psnr

    计算并报告平均PSNR（峰信噪比）。
-print_ssim

    计算并报告平均SSIM（结构相似度指标，请参阅 http://en.wikipedia.org/wiki/SSIM了解更多详细信息）。
-print_lsim

    计算并报告当地的相似性指标（最小误差之和并置的像素邻居之间）。
-进展

    报告编码％的进度。
-安静

    不打印任何东西。
-短

    只打印用于测试目的的简要信息（输出文件大小和PSNR）。

例子

cwebp -q 50 -lossless picture.png -o picture_lossless.webp
cwebp -q 70 picture_with_alpha.png -o picture_with_alpha.webp
cwebp -sns 70 -f 50 -size 60000 picture.png -o picture.webp
cwebp -o picture.webp -- ---picture.png


