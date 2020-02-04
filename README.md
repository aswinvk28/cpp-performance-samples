### Performance Primitives Exercise from Intel

This repository contains all the performance primities examples from 

- `SIMD`
- `OpenMP`
- `MPI`

The code samples uses `#pragma` declarations to conduct `MultiThreading`, `MultiProcessing`, `Instruction Set` tasks.

## Some tips

`#pragma omp declare simd`
this pragma vectorizes the function, which enables the instruction set to execute all in once. `SIMD` is single-instruction-multiple-data which implies the operations on the memory is done all at once using a single instruction. While making use of this function, you should be careful about the kind of operations to be executed. 

Such as for example a python data type cannot be executed directly as some decoding needs to be done internally. Whereas simple STL based data structured with `vector<int>`, `vector<float>` can be used for improving performance. 

Please read this article:
-------------------------

Vector emplace_back vs vector push_back:

[http://candcplusplus.com/c-difference-between-emplace_back-and-push_back-function](http://candcplusplus.com/c-difference-between-emplace_back-and-push_back-function)


## Vectorization

Code can be executed using Intel intrinsics, please refer to these API as mentioned below:

This is intrinsics guide for AVX2 instruction et architecture:

[https://software.intel.com/sites/landingpage/IntrinsicsGuide/#=undefined&techs=AVX2&expand=2297,3924](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#=undefined&techs=AVX2&expand=2297,3924)

## Parallization

`#pragma omp parallel num_threads(64)`

`#pragma omp for`

`#pragma omp parallel for`

`#pragma omp for simd`

`#pragma omp tasks`

Tasks are generally executed in a single thread, but there are exception in which you can use them.

##### Please refer to pragma directives for executing parallel tasks:

[https://www.ibm.com/support/knowledgecenter/SSGH2K_12.1.0/com.ibm.xlc121.aix.doc/compiler_ref/tuoptppp.html](https://www.ibm.com/support/knowledgecenter/SSGH2K_12.1.0/com.ibm.xlc121.aix.doc/compiler_ref/tuoptppp.html)

`#pragma omp single nowait`

Runs on a single thread without waiting for the coimpletion of thread execution

`#pragma omp master`

This is master thread

`#pragma omp taskwait`

`#pragma omp atomic`

`#pragma omp critical`

`#pragma omp barrier`

atomic, critical amd barrier are alternate representations of semaphores and mutexes

`#pragmna omp parallel sections`
{

}

When you enclose in parallel sections, the code gets executed within sections are executed simultaneously in parallel. This makes the programming easier, and eliminates the use of additional thread tasks to be created. 

`#pragma omp parallel`
{

}

The code within this section is ensured to be executed completely even though nowait is present. 

for exanple:
`#pragma omp parallel`
{
    `#pragma omp single nowait`
    {
        // code is executed without waiting
    }
    // code is executed after every thread joins
}

## MPI

This is based on popular OpenMPI framework,

Programming in C++ is quite tricky, whereas Python counterpart have easy paradigm. 

In MPI the compiler to be used is `mpigcc` 

Simple installation of `mpicc` or `mpigcc` is through conda

In this exercise, you can execute the code using `mpirun`

[https://www.open-mpi.org/doc/v4.0/man1/mpirun.1.php](https://www.open-mpi.org/doc/v4.0/man1/mpirun.1.php)
