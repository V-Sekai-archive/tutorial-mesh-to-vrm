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
