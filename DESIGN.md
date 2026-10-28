Hybrid Symbolic-Wave Architecture for Noisy Vectorization

Problem: Classical CV and pure DL approaches fail at robust vectorization of noisy, discontinuous contours. Integrals are computationally prohibitive; neural networks ignore deterministic geometry and require massive data.
Solution: A hybrid architecture combining Huygens-Fresnel wave propagation with symbolic topology extraction. Replaces pixel-level processing with node-level symbolic inference.
Key Architectural Decisions:
From Continuous Integrals to Discrete Wavefronts (FMM)
Instead of analytical integration over blurred edges, we model contour traversal as a Fast Marching Method. The "fire" propagates faster along high-confidence centers, naturally smoothing noise into scalable Bézier curves without explicit filtering.
Symbolic Fire on Topological Skeleton
We decouple detection from interpretation. A deterministic algorithm first extracts only critical nodes (intersections, endpoints). The symbolic AI then operates only on this sparse graph, avoiding combinatorial explosion on raw pixels.
Vector Jump ("Montenegro Method") for Gap Recovery
When topology is broken, the wavefront doesn't stop. It preserves spatial inertia (direction vector), constructs a search cone, and bridges gaps deterministically. This replaces probabilistic inpainting with physics-based extrapolation, making the system robust to occlusions and scanning artifacts.
Rejection of Pure Data-Driven Paradigm
The architecture explicitly avoids learning geometry from scratch. Instead, it encodes physical laws (wave propagation, vector continuity) as inductive biases. Result: CPU-efficient, interpretable, and generalizable without retraining on every new noise distribution.
Impact: Orders-of-magnitude reduction in compute vs. DL baselines. Deterministic behavior enables certification-critical applications where black-box NNs are unacceptable.
