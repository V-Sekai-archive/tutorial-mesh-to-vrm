# vox-to-vrm 

[![V-Sekai Vox to VRM Decisions](https://v-sekai.github.io/v-sekai-vox-to-vrm/log4brains/badge.svg)](https://v-sekai.github.io/v-sekai-vox-to-vrm/log4brains/)

# Purpose

Entry for meebitsDAO developer bounty for an automation tool to convert vox -> vrm.

# Workflow

1. Take a input .vox in T-Pose (not A-Pose). Reject all that are not in T-Pose.
1. Download Godot Engine 3.3
2. Open https://github.com/ClarkThyLord/Voxel-Core
3. Import .vox with the object mode. 
4. Import .vox also with uvs generated.
5. Import .vox also with centering above axis.  

![image](https://user-images.githubusercontent.com/32321/118209936-729f6780-b41e-11eb-9efb-999bc0a117fb.png)


7. Ensure scale is near 1.7 m for a humanoid (Try 0.05 scale).
8. Apply scale and only scale to mesh vertices.
9. Export Godot Engine scene as a glTF 2.0 binary. (custom engine)
10. Open gltf -> Blender (Use  Workflow Rignet)
12. Blender -> VRM

# Workflow VRM (Blender)

* Principled baker to bake vertex color
* xatlas options (use padding 16 for 1k textures or less)
* xatlas to create uv map (delete and rename UVMap0)
* use principled baker to bake (there's an option to overwrite if required.)
![image](https://user-images.githubusercontent.com/32321/118210174-ef324600-b41e-11eb-9892-d8b3d2a81127.png)
* Armature Viewport display: stick, names and in front.
* PROBLEMS WITH HAIR. The humanoids need to have acessories, hair and clothing removed.
* Install Saturday's VRM addon for Blender
* Assign all required bones (Hard!)
* Convert above baked base colour texture to both albedo and shade color.
* Export to vrm.
* Check animations in 3tene.

# Workflow Rignet

Checkout rignet to Blender folder.

1. conda create -n rignet python=3.7
1. conda init powershell
1. conda activate rignet
1. pip install numpy scipy matplotlib tensorboard open3d==0.9.0 opencv-python
1. pip install "rtree>=0.8,<0.9" # Note special method for windows!!!
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
7. Select mesh
8. Decimate
9. Density 0.8 and Threshold of 0.007
10. Wait a few minutes

![image](https://user-images.githubusercontent.com/32321/118210317-3ae4ef80-b41f-11eb-96c9-755fc54e3588.png)

## Used in other software

Problems with meshing and weighting.

3tene

https://user-images.githubusercontent.com/32321/118210676-a5962b00-b41f-11eb-8fa0-e81f99ebac5a.mp4

## Additional feature proposals

1. Automatic skeleton scanning in VRM for Blender
2. Automatic guessing of bones via location. Lasso them!
3. Better automatic rigs. Note the shoulder to spine problem.
