# Mesh Reconstruction and Simplification from Point Clouds
Implementation and tuning of algorithms which construct a mesh and simplify it from point clouds.

## Abstract
In this project, we explore various algorithms that (1) construct triangle meshes from point clouds (mesh reconstruction) and (2) reduce the number of triangles in meshes while preserving important topological features (mesh simplification). As an application, we apply these algorithms to the final point cloud output of Assignment 2: Epipolar Geometry in order to extract a triangle mesh from the two image views.

We first implement 2 different mesh reconstruction algorithms: "Alpha Shapes", and "Ball-Pivoting". We then implement several mesh simplification algorithms: "Vertex Removal", "Vertex Collapse", "Vertex Clustering", and "Quadric Decimation". We then compare the performances of the reconstruction algorithms and observe the impact of mesh simplification - both visually and by quantitatively measuring how close the output mesh is to the original point cloud/mesh. Finally, we feed the point cloud output of A2 into our mesh reconstruction/simplification pipeline and observe how well our mesh represents the image.

## Conclusions

The Alpha Shapes (AS) algorithm produces meshes without holes and runs quickly, but it is difficult to choose a correct value of  𝛼  to produce a mesh that resembles the point cloud. The Ball Pivoting algorithm (BPA) preserves the mesh shape better than AS, but produces large holes and takes a long time to run.

Based on the visual and quantitative comparisons of the four closely-related simplification algorithms, quadric decimation is the slowest while vertex clustering is the fastest in terms of runtime efficiency. With regards to topological preservation, quadric decimation is the best at keeping a model shape while vertex removal is the worst. Overall, we find that vertex clustering is good enough for fast, moderate quality simplification, while quadric decimation is optimal for precise models.

Overall, we find that the combination of SR and quadric decimation produces the best simplified meshes from our tests.

However, the result of applying our mesh reconstruction and simplification algorithms on the point cloud produced by A2: Epipolar Geometry is not great. Although we can preserve the general shape of the structure, many of the finer details are not present. This is because the density of the point cloud is not very high. If we could somehow produce more point samples, then we hypothesize that our resulting mesh would be better.

As an extension of our work, we could explore more state-of-the-art mesh reconstruction techniques such as Poisson Surface Reconstruction. We can also try to apply our methods to the multi-view volumetric photo reconstruction problem, that is, we can generate a simplified triangle mesh from multiple images of an object from different views.
