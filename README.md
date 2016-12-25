# T_T
Texture_Transcoder......Transcode kinds of annoying texture data to GPU support format real-time.

So many mobile-device support compress texture format:
          
          Tegra/Vivante-—----DXTC
          Adreno-------------ATC
          PowerVR------------PVRTC
          GLES3--------------ETC2/ASTC
          GLES2--------------ETC1
          
For texture no alpha channel, we can convert textures to ETC1 offline, all devices > gles2 wiil support. 

If texture has alpha channel:

          use RGBA8---------------------------------------too many memory and bandwidth
          use RGBA4---------------------------------------most time not good enough 
          use ETC1 for RGB, the other ETC1/A8 for alpha---need two texture sample in shader
          use DXT5/ATC_RGBA/EAC/....----------------------only parts of devices support, others decode to RGBA8
