# Mesh

This folder contains the mesh used for the **supersonic flow around a circular cylinder** case.

- The mesh was created in **ANSYS Fluent** and exported in Fluent (`.msh`) format.
- To use it in **OpenFOAM**, first copy the mesh file into your case directory and run:

```bash
fluentMeshtoFOAM <mesh_file.msh>
