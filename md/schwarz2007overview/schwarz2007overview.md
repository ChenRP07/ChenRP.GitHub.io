# Overview of Scalable Video Coding Extension of the H.264/AVC Standard
## Introduction
现代的视频传输存储系统基于RTP/IP网络，而RTP/IP网络具有广泛的连接质量和接收设备，从智能手机上的小屏幕到高性能PC上的高分辨率屏幕等。分级视频编码（SVC）用于解决视频系统中质量差异的问题，SVC包含一个或多个子集比特流，比特流可以使用H.264等编码器进行解码并拥有一致的数据量。然而SVC拓展很少被使用，原因在于SVC的分级特性伴随着编码效率的明显损失以及解码器复杂度的显著提高。此外联播多个码流和视频转码功能也可以实现类似SVC的效果，因此SVC也需要和他们竞争。
## Type of Scalability, Applications, and Requirements
可伸缩性就是从视频流中去除一部分数据，该流仍可以解码，视觉质量低于完整的流但是高于继续去除后的流，不具备可伸缩性的流称为单层比特流。通常来讲，可伸缩性包括空间（图片大小）、时间（帧率）和质量（SNR）。在SVC下源数据只需编码一次以获得最高的分辨率和比特率，产生可伸缩的比特流，通过丢弃特定数据获取分辨率、质量较低的表示。在监控应用中，使用SVC的视频可以在一段时间后删除掉高质量的部分，只留下低质量的部分供长期存档。
虽然SVC有很多优点，但是空间和质量伸缩始终以增加解码器复杂度和降低编码效率为代价，因此很少使用。但是时间伸缩可以提高编码效率，因此通常使用这种形式。SVC要做到以下几点
$\bullet$ 每个SVC子集具有和单层编码近似地编码效率。
$\bullet$ 解码器的复杂度增加很少。
$\bullet$ 支持时间、空间、质量可伸缩。
$\bullet$ 支持向后兼容的基础层，例如H.264
$\bullet$ 编码后支持简单的比特流自适应。

## H.264/AVC Basis
SVC作为AVC的拓展进行标准化。AVC的设计包括了视频编码层VCL和网络抽象层NAL，VCL创建源视频的编码表示，NAL格式化这些数据使VCL数据能够被各种系统利用。

## Basic Concepts for Extending H.264/AVC Towards and SVC Standard
### Temporal Scalability

