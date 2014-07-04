This strong scaling profile was done using 4 processes per node and forced Strong Dirichlet conditions.

The SuperLU direct solver was used with the following options

```
-rans2p_ksp_type preonly -rans2p_pc_type lu -rans2p_pc_factor_mat_solver_package superlu_dist
-ncls_ksp_type   preonly -ncls_pc_type   lu -ncls_pc_factor_mat_solver_package   superlu_dist
-vof_ksp_type    preonly -vof_pc_type    lu -vof_pc_factor_mat_solver_package    superlu_dist
-rdls_ksp_type   preonly -rdls_pc_type   lu -rdls_pc_factor_mat_solver_package   superlu_dist
-mcorr_ksp_type  preonly -mcorr_pc_type  lu -mcorr_pc_factor_mat_solver_package  superlu_dist
-kappa_ksp_type preonly -kappa_pc_type lu -kappa_pc_factor_mat_solver_package superlu_dist
-dissipation_ksp_type preonly -dissipation_pc_type lu -dissipation_pc_factor_mat_solver_package superlu_dist
```

There were crashes in the partitioning for 16 processes.  These were not investigated.

Here is the performance summary:

np | (s)
---|-----
  1|  2139
  2|  1704
  4|  1301
  8|  1642
 16| crashed after: Global Exterior Element Boundary Quadrature
 32| 1769
 64| 1785
128| crashed after:Global Exterior Element Boundary Quadrature
256| (also appears to have crashed)