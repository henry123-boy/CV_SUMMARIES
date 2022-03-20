# Pose-free works
+ barf https://chenhsuanlin.bitbucket.io/bundle-adjusting-NeRF/

  pre-processing: 
  
                 1、centralization of the poses;
  
                 2、the different weights for different frequency bands (very vital trick for performance);

  weakness: 
                 1、slow inference speed;
                 
                 2、bad geometry accuracy especially transfer its depth map into pointclouds;

                 3、the same cost time to origianl nerf, which is around 6s to render a 640*480 image;
  
  strengthness:
  
                 1、relative good pose estimation; (which does not use any matching methods);
                 
                 2、the project owns a very clear and rational structure;
                 
  notes:
  
                 1、during the test-time, barf can do the optimization for better rendering results, cause the poses provided by colmap may not correspond to the trained barf (colmap pose may be inaccurate); if you ban the test optimization, it will cause the disalignment for the gt and renderred;
                 
+ NeRF--
+ NeRF++

# Generalized works

+ pixnerf https://github.com/sxyu/pixel-nerf


# Other Representation for Filed

## Feature Grid

+ NICESLAM
+ Plenoctree
+ Plenoxel

## MLP

+ NeRF
+ UNISURF

## Tensorial Representation

+ TensoRF: Tensorial Radiance Fields

**Comments**: without any doubt, the MLP is the most compat representation for a scene, whose complexness is o(1) and this is also the powerful advantage for implicit representation; and 3D grid explicitly represents a scene by o(N3) grid; However, the grid is actually a kind of tensor, so in the TensoRF, the author naturally uses the tensor decomposition techniques to reduce the complexity from o(N3) to o(N2) or o(N1).
