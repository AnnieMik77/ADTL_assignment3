# Learning Self-Prior for Mesh Inpainting using Self-Supervised Graph Convolutional Network (TBD)

## Usage

### Installation (TBC)

```
git clone https://github.com/astaka-pe/xxx
cd xxx
conda env create -f environment.yml
conda activate yyy
```

### Preperation

- Unzip `datasets.zip`
- Sample meshes will be placed in `datasets/`
- Put your own mesh in a new arbitrary folder as:
    - Deficient mesh: `datasets/**/{mesh-name}/{mesh-name}_original.obj`
    - Ground truth: `datasets/**/{mesh-name}/{mesh-name}_gt.obj`
- The deficient and the ground truth meshes need not share a same connectivity but their scales must be shared

### Preprocess

- Specify the path of the deficient mesh
- Create **initial mesh** and **smoothed mesh**

```
python preprocess/prepare.py -i datasets/**/{mesh-name}/{mesh-name}_original.obj
```
- options
    - `-r {float}`: Target length of remeshing. The higher the coarser, the lower the finer. `default=0.6`.

- Computation time: 30 sec

### Training

```
python sgcn.py -i datasets/**/{mesh-name}   # SGCN
python mgcn.py -i datasets/**/{mesh-name}   # MGCN
```

- options
    - `-CAD`: For a CAD model
    - `-real`: For a real scan
    - `-cache`: For using cache files (for faster computation)
    - `-mu` : Weight for refinement

### Evaluation

- Create `datasets/**/{mesh-name}/comparison` and put meshes for evaluation
    - A deficient mesh `datasets/**/{mesh-name}/comparison/original.obj` and a ground truth mesh `datasets/**/{mesh-name}/comparison/gt.obj` are needed for evaluation

```
python check/batch_dist_check.py -i datasets/**/{mesh-name}
```

- options
    - `-real`: For a real scan

## Run other competitive methods

### MeshFix [Attene 2010]

```
python meshfix.py -i datasets/**/{mesh-name}
```

### Context-based Coherent Surface Completion [Harary+ 2014]

```
conda activate tinymesh
python context_fill.py -i datasets/**/{mesh-name}
```