# Rondeau Nsight Systems: MPI and NCCL at Δt = 0.005 s

Updated 2026-11-09 14:53 EST. **WAITING_FOR_BENCHMARK**; 0/6 requested cases complete.

Both compressible explicit and split-explicit dynamics use Float32, WENO5, the full dry CBL setup,
10 warmup steps, then exactly 10 captured main steps at Δt = 0.005 s. Split-explicit uses 12 acoustic substeps.
The one-GPU grid is 512×512×512; the four-GPU grid is 1024×1024×512 (512³ cells/GPU).
Each dynamics has one shared plain-GPU serial baseline. Four-GPU MPI/NCCL use the faster observed
partition separately for each dynamics/backend, selected from finite 4×1 and 2×2 rerun cases.

The controller waits for the entire [unprofiled rerun](../weak_scaling_mpi_nccl_2026-11-09_dt0p005/README.md) and its final validation
before starting, then waits for the selected devices to have no compute processes. Profiled timings include
profiling overhead and remain separate from unprofiled benchmark timings.

## Capture locations

Paths below are exact absolute paths on Rondeau. Pending paths are planned locations, not existing results.

| Dynamics | Backend | GPUs | Partition | State | Rank | Nsight result file | Size (MiB) |
|---|---|---|---|---|---|---|---|
| compressible_explicit | SERIAL | 1 | 1×1 | PENDING | 0 | `/local_scratch/ajtse/breeze_nsight_mpi_nccl_2026-11-09/profiles/compressible_explicit_SERIAL_1g/rank_0/profile.nsys-rep` | pending |
| compressible_explicit | MPI | 4 | awaiting rerun | PENDING | 0 | `/local_scratch/ajtse/breeze_nsight_mpi_nccl_2026-11-09/profiles/compressible_explicit_MPI_4g/rank_0/profile.nsys-rep` | pending |
| compressible_explicit | MPI | 4 | awaiting rerun | PENDING | 1 | `/local_scratch/ajtse/breeze_nsight_mpi_nccl_2026-11-09/profiles/compressible_explicit_MPI_4g/rank_1/profile.nsys-rep` | pending |
| compressible_explicit | MPI | 4 | awaiting rerun | PENDING | 2 | `/local_scratch/ajtse/breeze_nsight_mpi_nccl_2026-11-09/profiles/compressible_explicit_MPI_4g/rank_2/profile.nsys-rep` | pending |
| compressible_explicit | MPI | 4 | awaiting rerun | PENDING | 3 | `/local_scratch/ajtse/breeze_nsight_mpi_nccl_2026-11-09/profiles/compressible_explicit_MPI_4g/rank_3/profile.nsys-rep` | pending |
| compressible_explicit | NCCL | 4 | awaiting rerun | PENDING | 0 | `/local_scratch/ajtse/breeze_nsight_mpi_nccl_2026-11-09/profiles/compressible_explicit_NCCL_4g/rank_0/profile.nsys-rep` | pending |
| compressible_explicit | NCCL | 4 | awaiting rerun | PENDING | 1 | `/local_scratch/ajtse/breeze_nsight_mpi_nccl_2026-11-09/profiles/compressible_explicit_NCCL_4g/rank_1/profile.nsys-rep` | pending |
| compressible_explicit | NCCL | 4 | awaiting rerun | PENDING | 2 | `/local_scratch/ajtse/breeze_nsight_mpi_nccl_2026-11-09/profiles/compressible_explicit_NCCL_4g/rank_2/profile.nsys-rep` | pending |
| compressible_explicit | NCCL | 4 | awaiting rerun | PENDING | 3 | `/local_scratch/ajtse/breeze_nsight_mpi_nccl_2026-11-09/profiles/compressible_explicit_NCCL_4g/rank_3/profile.nsys-rep` | pending |
| compressible_splitexplicit | SERIAL | 1 | 1×1 | PENDING | 0 | `/local_scratch/ajtse/breeze_nsight_mpi_nccl_2026-11-09/profiles/compressible_splitexplicit_SERIAL_1g/rank_0/profile.nsys-rep` | pending |
| compressible_splitexplicit | MPI | 4 | awaiting rerun | PENDING | 0 | `/local_scratch/ajtse/breeze_nsight_mpi_nccl_2026-11-09/profiles/compressible_splitexplicit_MPI_4g/rank_0/profile.nsys-rep` | pending |
| compressible_splitexplicit | MPI | 4 | awaiting rerun | PENDING | 1 | `/local_scratch/ajtse/breeze_nsight_mpi_nccl_2026-11-09/profiles/compressible_splitexplicit_MPI_4g/rank_1/profile.nsys-rep` | pending |
| compressible_splitexplicit | MPI | 4 | awaiting rerun | PENDING | 2 | `/local_scratch/ajtse/breeze_nsight_mpi_nccl_2026-11-09/profiles/compressible_splitexplicit_MPI_4g/rank_2/profile.nsys-rep` | pending |
| compressible_splitexplicit | MPI | 4 | awaiting rerun | PENDING | 3 | `/local_scratch/ajtse/breeze_nsight_mpi_nccl_2026-11-09/profiles/compressible_splitexplicit_MPI_4g/rank_3/profile.nsys-rep` | pending |
| compressible_splitexplicit | NCCL | 4 | awaiting rerun | PENDING | 0 | `/local_scratch/ajtse/breeze_nsight_mpi_nccl_2026-11-09/profiles/compressible_splitexplicit_NCCL_4g/rank_0/profile.nsys-rep` | pending |
| compressible_splitexplicit | NCCL | 4 | awaiting rerun | PENDING | 1 | `/local_scratch/ajtse/breeze_nsight_mpi_nccl_2026-11-09/profiles/compressible_splitexplicit_NCCL_4g/rank_1/profile.nsys-rep` | pending |
| compressible_splitexplicit | NCCL | 4 | awaiting rerun | PENDING | 2 | `/local_scratch/ajtse/breeze_nsight_mpi_nccl_2026-11-09/profiles/compressible_splitexplicit_NCCL_4g/rank_2/profile.nsys-rep` | pending |
| compressible_splitexplicit | NCCL | 4 | awaiting rerun | PENDING | 3 | `/local_scratch/ajtse/breeze_nsight_mpi_nccl_2026-11-09/profiles/compressible_splitexplicit_NCCL_4g/rank_3/profile.nsys-rep` | pending |

Each completed rank also has `profile.sqlite` beside its `.nsys-rep` for trace validation.
The [profile manifest](profile_manifest.json) records sizes, SHA-256 hashes, SQLite paths and captured kernel counts.

## Reproduction and validation

The scientific source and resolved environment match the unprofiled rerun. Profiling uses an isolated
checkout at `/local_scratch/ajtse/breeze_nsight_mpi_nccl_2026-11-09/source`; the tracked driver adds an optional `--profile=true` capture range.
The main checkout and active benchmark source are left unchanged. [Driver patch](provenance/profile_driver.patch),
[source revision](provenance/source_commit.txt), [environment](provenance/environment.log),
[study state](study.json), [exact commands](execution/commands.log), [controller log](execution/controller.log).

Nsight traces CUDA, MPI (Open MPI), and NVTX. CPU sampling and context-switch tracing are disabled.
CUDA profiler start/stop brackets only the requested time steps and their final device synchronization;
construction, warmup/JIT, and post-run field checks are outside the capture. This Nsight version has no
dedicated NCCL API trace option; NCCL activity appears through CUDA kernels and any library NVTX ranges.

Before the six requested captures, separate small-grid serial-explicit and two-rank NCCL split-explicit
pilots validate capture/export and finite fields. They are recorded under `pilots/` and excluded from the six-case count.
Every requested case requires finite prognostic and velocity fields on every rank, a successful profiler exit,
a nonempty `.nsys-rep`, and a nonempty CUDA kernel table in each exported SQLite database.
GPU/process samples verify device assignment and loaded MPI/NCCL libraries. These checks establish
capture validity and field finiteness; they do not compare distributed model solutions with a serial solution.

No plots are generated for Nsight runs. Raw captures stay in local scratch; this README lists their locations.

From the repository root, launch a fresh study after choosing a new study/scratch directory:

```bash
source /u/ajtse/Breeze.jl/benchmarking/results/rondeau/nsight_mpi_nccl_2026-11-09_dt0p005/execution/environment.sh
python3 -u /u/ajtse/Breeze.jl/benchmarking/results/rondeau/nsight_mpi_nccl_2026-11-09_dt0p005/execution/run_profiles.py > /u/ajtse/Breeze.jl/benchmarking/results/rondeau/nsight_mpi_nccl_2026-11-09_dt0p005/execution/controller.log 2>&1
```

The controller refuses an existing study to avoid duplicate captures.
