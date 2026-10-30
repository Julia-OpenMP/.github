# OpenMP APIs in Julia

This organization works on a support for [OpenMP](https://www.openmp.org/) APIs in [Julia](https://julialang.org/) through the [omp.jl package](https://github.com/Julia-OpenMP/omp.jl).

## Disclaimer
This organization is an independent research group. It **is not** affiliated with the JuliaHub, Inc. or the OpenMP ARB.
All projects are currently in early development stages.
If you are interested, please reach-out! :-) 

## Motivations
The ecosystem for performant and portable parallel programming in Julia is **sparse**.
The language has built-in support for [threads and tasking](https://github.com/JuliaLang/julia), but [performance issues](https://discourse.julialang.org/t/overhead-of-threads-threads/53964/) often lead HPC users to adopt alternatives.
Popular alternatives include [Polyester.jl](https://github.com/JuliaSIMD/Polyester.jl), [ThreadPinning.jl](https://github.com/carstenbauer/ThreadPinning.jl), [KernelAbstractions.jl](https://github.com/JuliaGPU/KernelAbstractions.jl), [JACC](https://github.com/JuliaGPU/JACC.jl). This creates a fragmented, incomplete software ecosystem.

OpenMP is a general-purpose parallel programming API, developed jointly by research laboratories and the industry.
Its [specifications](https://www.openmp.org/specifications/) and implementations (e.g., [LLVM](https://github.com/llvm/llvm-project/), [GCC](https://github.com/gcc-mirror/gcc) have passed the test of time.

This organization aim to bridge both world, by providing **OpenMP support in Julia** *(or was it Julia support in OpenMP?)*.

## Examples
```Julia
s = 0.0

// Option A
@omp parallel for reduction(+, s) for i in eachindex(x)
    s += x[i]^2
end

// Option B
@omp parallel for reduction(+, s) begin
    for i in eachindex(x)
        s += x[i]^2
    end
end
```

## Contact
Romain Pereira (rpereira@anl.gov)
