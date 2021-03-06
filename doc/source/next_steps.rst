Next Steps
==========

Use of Finite Elements
----------------------

The studies with the Ritz Method presented in module
:mod:`compmech.conecyl` have shown the main disadvantages regarding
the numerical integration of the non-linear stiffness matrices:

- since the approximation functions are complex, the evaluation of each
  integration point is expensive

- there is no quadrature rule available for such complex functions

Moreover, the use of very especialized models makes it difficult to extend
their applicability for different cases where different load and boundary
conditions are desired.

The use of finite elements will allow the use of simpler approximation
functions significantly reducing the computational cost to evaluate each
integration point, and allowing the application of quadrature rules,
minimizing the number of integration points required.

Building the Spine
..................

Before implementing the new finite elements a very well defined process
must be stablished in order to define:

- integration with pynastran to read NASTRAN input files

- define node class

- define element class

- node-element connectivity schemes:

  - minimize band-width of the stiffness matrices by working with a proper
    internal node identification. The user will use the conventional node ID,
    but the analysis could use an internal ID that is calculated to minimize
    the band-width of the sparse matrices

- use of C++, C or Cython?

  - use Cython or Python classes?

- possible sparse solvers:

  - Intel MKL PARDISO
  - the ``scipy.sparse`` solver, at least to build the ``csr_matrix``
    or ``csc_matrix``
  - SuperLU
  - ARPACK (used in ``scipy.sparse.linalg.eigsh``)
  - Use the rainflow algorithm?

- Use SIMD programming for common array operations?

  - rely on NumPy, with a group working on these optimizations
  - use Eigen3 wrappers such as minieigen

Developing New Elements
.......................

The element types should include some of those available in NASTRAN plus
some additional options:

- The priority order should be:

  - CQUAD4 - plate element like in NASTRAN
  - ZQUAD4 - cylindrical (Zylinder) shell element
  - KQUAD4 - conical (Konus) shell element
  - 1-D elements
  - 3-D elements

- The element's formulation should allow:
  - Initial Imperfection (how?!)
  - CLPT
  - FSDT
  - TSDT

Studies
.......

The new tools will create a high potential for new studies concerning
advanced procedures to calculate shear correction factors, new non-linear
methods and so on...

GPU
---

How to use GPU-based programming?

Some preliminary studies show that it is promising to apply such programming
strategies to largely parallelize operations like the numerical integration of
each element's stiffness matrix... each thread could be one element being
integrated for example and this should be benchmarked against a CPU-based
integration using Shared-Memory Parallel programming through OpenMP, which has
already been applied in :mod:`compmech.conecyl`.


