# U-NET-for-Caffe
U-Net with upsampling layer under caffe
1. copy the src/caffe/layers/upsample_layer.cpp and src/caffe/layers/upsampling_layer.cu and include/caffe/layers/upsample_layer.h to your caffe
2. edit the src/caffe/proto/caffe.proto
   add a declaration of parameters used in upsample_layer and give the parameter a unique ID 
   add a line inside message LayerParameter {} 
   
   // Parameter for upsample_layer.
   optional UpsampleParameter upsample_param = 152;
  
   add a line after  message LayerParameter {}
   // message for upsample parameter 
   message UpsampleParameter {
   optional int32 scale = 1 [default = 1];
   }
3. re-build the source code of caffe in vs.
   if you use python interference, don't forget copy the released file in \Build\x64\Release\pycaffe\caffe to site-packages of python      path.
4. I modified the prototxt file of unet network with deconvolution layer, because its params are difficult to initialize.
   I always have trouble in training deconvolution layer.
   the deconvolution layer is replaced by upsampling layer + convolution layer with 2*2 kernel, which is as same structure as unet in keras.
6. you can try your own data now!
