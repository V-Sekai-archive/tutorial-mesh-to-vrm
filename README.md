# vox-to-vrm 

[![V-Sekai Vox to VRM Decisions](https://v-sekai.github.io/v-sekai-vox-to-vrm/log4brains/badge.svg)](https://v-sekai.github.io/v-sekai-vox-to-vrm/log4brains/)

# Purpose

Entry for meebitsDAO developer bounty for an automation tool to convert vox -> vrm.

# Workflow

1. Take a input .vox in T-Pose (not A-Pose). Reject all that are not in T-Pose.
1. Download Godot Engine 3.3
2. Open https://github.com/ClarkThyLord/Voxel-Core
3. Import .vox with first the object mode. 
4. Import .vox with second uvs generated.
5. Import .vox with centering above axis.  
7. Ensure scale is near 1.7 m for a humanoid (Try 0.05 scale).
8. Apply scale and only scale to mesh vertices.
9. Export Godot Engine scene as a glTF 2.0 binary.
10. ??? Open gltf -> Blender (Use auto rig)
11. ??? Blender -> VRM (Blender. blocked on t-posing)

# Workflow Rignet

Checkout rignet to Blender folder.

1. conda create -n rignet python=3.7
1. conda init powershell
1. conda activate rignet
1. pip install numpy scipy matplotlib tensorboard open3d==0.9.0 opencv-python
1. pip install "rtree>=0.8,<0.9" 
1. pip install trimesh[easy]
1. conda install pytorch==1.6.0 torchvision==0.7.0 cudatoolkit=10.1 -c pytorch
1. pip install torch-scatter -f https://pytorch-geometric.com/whl/torch-1.6.0+cu101.html
1. pip install torch-sparse -f https://pytorch-geometric.com/whl/torch-1.6.0+cu101.html
1. pip install torch-cluster -f https://pytorch-geometric.com/whl/torch-1.6.0+cu101.html
1. pip install torch-spline-conv -f https://pytorch-geometric.com/whl/torch-1.6.0+cu101.html
1. pip install torch-geometric
2. scoop\apps\blender\current\2.92\python\bin> python -m pip install pillow # Is this needed?
3. Use conda list to get the location of the modules folder for conda's rignet env.
4. Install brignet Blender addon.
5. Configure the rignet env from above and the brignet folder and the rignet folder under brignet.
6. There is a typo in brignet\rignetconnect.py at `parent, key, init_id = primMST_symmetry(cost_matrix, root_id, pred_joints)`

