# PureDigits_OCR_Openvino

This is constructed under PaddleOCR and compiled in OpenVino for x86 architecture.

This repo include two computer vision models

- a three-stage OCR algorithm
  - Stage 1 (not included, please see the corresponding repo on my Github)
    - Stage 1a : YoLoV8 with large-scale iterated transformers to track the corresponding txts.
    - Stage 1b : Use credibility interval (computed from statistical sampling techiques) to make accurate inference on the detected txt
    - Stage 1c : Use CV2 to clip the non-txt part out
  - Stage 2 : Paddle OCR in OpenVino
    - Stage 2a : Training or transfer learning the PaddleOCR on your data (MRCNN/EfficientNet for detection and ABInet for recognition)
    - Stage 2b : Compile and quantize your model in OpenVino for fast deployment using int. (Quantization not included due to it simplicity)
    - Stage 2c : OpenVino inference on the cropped txt image using mobile/edge device (webcam) and cloud inference
  - Stage 3 : Time series modelling
    - Stage 3a : Holter-Winters Smoothing on the detected signal using 1D Gaussian Kernel for denoising (not included, please see the corresponding repo on my Github)
    - Stage 3b : Maximum Likelihood or A Posteriori estimation on the time series
    - Stage 3c : Final inference.