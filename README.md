# Enhancing 3D medical mesh completion with Self-Prior Graph Convolutional Networks

This repository contains:

- the code of the reference paper we use: Self-Prior Graph Convolutional Networks.
Their README file is moved to [README_original.md](README_original.md).

- results of our experiments on MedShapeNet dataset in [dataset/medical/](dataset/medical/) folder.

## Experiments on MedShapeNet
Each result folder `dataset/medical/example` contains:
- `example_gt`: ground truth mesh without holes
- `example_original`: mesh with a hole
- `example_initial`: mesh repaired by MeshFix
- `output/*/xx_step.obj`: mesh repaired by SGCN at xx-th step
- `output/*/refine.obj`: mesh repaired by SGCN after refinement
- `output/*/all=xxx-hole=yyy-refine.ply`: mesh repaired by SGCN after refinement, colored version. `xxx` is the e_all value, `yyy` is the e_hole value.

