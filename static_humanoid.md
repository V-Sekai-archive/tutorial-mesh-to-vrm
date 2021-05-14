# vox-to-vrm 

[![V-Sekai Vox to VRM Decisions](https://v-sekai.github.io/v-sekai-vox-to-vrm/log4brains/badge.svg)](https://v-sekai.github.io/v-sekai-vox-to-vrm/log4brains/)

# Purpose

Go from a static mesh to a fully animated VRM avatar.

# Workflow

1. Take an input mesh in T-Pose (not A-Pose). Reject all that is not in T-Pose.
7. Ensure the scale is near 1.7 m for a humanoid.
8. Apply scale and only scale to mesh vertices.
9. Export the Godot Engine scene as a glTF 2.0 binary. (custom engine)
10. Open gltf -> Blender (Use Workflow Rignet)
12. Blender -> VRM

# Workflow Rignet

Check out Rignet to Blender folder.

1. conda create -n rignet python=3.7
1. conda init powershell
1. conda activate rignet
1. pip install numpy scipy matplotlib tensorboard open3d==0.9.0 opencv-python
1. pip install "rtree>=0.8,<0.9" # Note unique method for Microsoft Windows 10. See Rignet readme.
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
8. Decimate to 3600 to 4000 polygons.
9. Density 0.8 and Threshold of 0.007
10. Disable downscale skinning.
11. There is symmetry on X (Blender axis convention.)
12. Wait a few minutes
13. Check for the non-existance of weird bone branches.
14. Replace the skinning with voxel diffuse skinning.
1. Principled baker to bake vertex colour
1. xatlas options (Use padding of 16 for when around 1k textures.)
1. xatlas to create UV map (delete and rename UVMap0)
1. use principled baker to bake (there is an option to overwrite if required.)
1.[image](https://user-images.githubusercontent.com/32321/118210174-ef324600-b41e-11eb-9892-d8b3d2a81127.png)
1. Armature Viewport display: stick, names and in front.
1. PROBLEMS WITH HAIR. The humanoids need to have accessories, hair and clothing removed.
1. Install Saturday's VRM addon for Blender
1. Assign all required bones (Hard!)
1. Convert above baked base colour texture to both albedo and shade colour.
1. Export to VRM.
1. Check animations in 3tene.

## Used in other software

3tene

## Additional feature proposals

1. Automatic skeleton scanning in VRM for Blender
2. Automatic guessing of bones via location. Lasso them!
3. Better automatic rigs. Note the shoulder to a spine problem.
