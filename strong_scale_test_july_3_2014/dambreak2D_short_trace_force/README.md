This strong scaling profile was done using 4 processes per node and forced Strong Dirichlet conditions.

The ASM preconditioner was run with the following options:

```
-rans2p_ksp_type fgmres -rans2p_ksp_gmres_restart 200 -rans2p_ksp_gmres_modifiedgramschmidt
-rans2p_pc_type fieldsplit
-rans2p_pc_fieldsplit_type schur -rans2p_pc_fieldsplit_schur_fact_type upper -rans2p_pc_fieldsplit_schur_precondition a11
-rans2p_fieldsplit_velocity_ksp_type preonly
-rans2p_fieldsplit_velocity_pc_type asm -rans2p_fieldsplit_velocity_pc_asm_type basic
-rans2p_fieldsplit_pressure_ksp_type preonly
-rans2p_fieldsplit_pressure_pc_type hypre -rans2p_fieldsplit_pressure_pc_hypre_type boomeramg
-ncls_ksp_type   fgmres -ncls_pc_type   hypre -ncls_pc_hypre_type   boomeramg
-vof_ksp_type    fgmres -vof_pc_type    hypre -vof_pc_hypre_type    boomeramg
-rdls_ksp_type   fgmres -rdls_pc_type   hypre -vof_pc_hypre_type    boomeramg
-mcorr_ksp_type  cg     -mcorr_pc_type  hypre -mcorr_pc_hypre_type  boomeramg
```

There were crashes in the partitioning for 16 processes.  These were not investigated.

Here is the performance summary:

np | (s)
---|-----
 1 | 1036
 2 |  4768
 4 |  4030
 8 |  4634
16 | crashed after: Global Exterior Element Boundary Quadrature
32 | 4226
64 | (Did not complete)
128| (Did not run)