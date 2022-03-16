# Pose-free works
+ barf https://chenhsuanlin.bitbucket.io/bundle-adjusting-NeRF/

  pre-processing: 
  
                 1、centralization of the poses;
  
                 2、the different weights for different frequency bands (very vital trick for performance);

  weakness: 
                 1、slow inference speed;
                 
                 2、bad geometry accuracy especially transfer its depth map into pointclouds;
  
  strengthness:
  
                 1、relative good pose estimation; (which does not use any matching methods)
                 
+ NeRF--
+ NeRF++

# Generalized works

+ pixnerf https://github.com/sxyu/pixel-nerf
