# cs610-assignment-4-solved



**<span style='color:red'>TO GET THIS SOLUTION VISIT:</span>** https://www.ankitcodinghub.com/product/cs610-general-policies-solved-8/

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;128535&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;2&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (2 votes)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CS610 Assignment 4 Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">
            
<div class="kksr-stars">
    
<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
    
<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>
                

<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (2 votes)    </div>
    </div>
• You should do this assignment alone.

• Do not copy or turn in solutions from other sources. You will be penalized if caught.

• You can tweak the compilation commands in the Makefile to suit your compiler version and the target architecture. Include the updated Makefile with exact compilation instructions for each programming problem (e.g., arch and code flags to nvcc).

• Refer to the CUDA C++ Programming Guide for documentation on the CUDA APIs and their uses.

Submission

• Submission will be through Canvas.

• Submit a compressed file called “⟨roll⟩-assign4.tar.gz”. The compressed file should have the following structure.

— roll

— — roll-assign4.pdf

— — &lt;problem1-dir&gt;

— — — &lt;source-files&gt; — — &lt;problem2-dir&gt;

— — — &lt;source-files&gt; — — &lt;problem3-dir&gt;

— — — &lt;source-files&gt; — — &lt;problem4-dir&gt;

— — — &lt;source-files&gt;

• We encourage you to use the LATEX typesetting system for generating the PDF file. You can use tools like Tikz, Inkscape, or Draw.io for drawing figures if required. You can alternatively upload a scanned copy of a handwritten solution, but make sure the submission is legible.

• You will get up to two late days to submit your assignment, with a 25% penalty for each day.

Evaluation

• Write your programs such that the exact output format (if any) is respected.

• We will primarily use the GPU3 department server for evaluation.

Consider the following code.

#define N 64 double in[N][N][N], out[N][N][N]; for (i=1; i&lt;N-1; i++) {

for (j=1; j&lt;N-1; j++) {

for (k=1; k&lt;N-1; k++) { out[i][j][k]=0.8 * (in[i-1][j][k] + in[i+1][j][k] + in[i][j-1][k] + in[i][j+1][k] + in[i][j][k-1] + in[i][j][k+1]);

}

}

}

1

2

3

4

5

6

7

8

9

10

The above computation pattern is referred to as stencil pattern. In the stencil pattern, the value of a point is a function of the eight neighboring points (three in row i −1, two in row i, and three in row i +1). In the above listing, the access pattern has reuse on the array in in 3 dimensions.

You will implement five versions of the above stencil pattern. Your goal is to strive for getting as much speedup as possible with the second optimized kernel. Compare the performance of the different kernel versions, and explain your observations. Initialize the elements of in with random values.

(i) Implement a naïve CUDA kernel (i.e., no optimizations are required) that implements the above code.

(ii) Use shared memory tiling to improve the memory access performance of the code. Investigate and describe how the size of the block/tile computed by each thread block influences the performance. Experiment with blocks with sides comprising values from the set {1,2,4,8},

(iii) Implement other loop transformations like loop unrolling and loop permutation over version (ii). Explain your optimizations and highlight their impact.

(iv) Implement version (iii) using pinned memory (e.g., cudaHostAlloc(…, cudaHostAllocDefault)).

(v) Implement version (iii) using unified virtual memory (e.g., cudaMallocManaged()).

Use cudaEvent APIs for timing kernels and different CUDA functions. You should use tools like nvprof, nvvp, or ncu to justify your results. Nvprof should suffice, although NVIDIA now recommends using Nsight Compute or Nsight Systems.

Implement the exclusive prefix sum algorithm with CUDA for unsigned integer type. You are allowed to port any known parallel algorithm to CUDA. NVIDIA provides a “parallel algorithms” library called Thrust that is similar in spirit to C++ STL. Write a function to use Thrust’s prefix sum algorithms to check for the correctness of your implementation.

We will test your code for correctness and performance on random input arrays.

Parallelize the attached C code (problem3-v0.c) using CUDA. You will implement three versions.

1. The first version will be a vanilla port of the C code. Your goal in this version is to ensure correctness. The challenges are in mapping the large iteration space of the 10D loop nest and writing back the output data from the device to the host. Implementing optimizations is optional.

2. Improve the performance of version (i) using different possible optimizations (e.g., shared memory tiling, launch multiple kernels, data prefetching and memadvise).

3. Implement the C code with UVM support with CUDA.

4. Implement a version using different transformations provided by Thrust. A few Thrust transformations are well-suited for the given problem.

Compare the performance of the four versions.

Convolution is an array operation where each output data element is a weighted sum of a collection of neighboring input elements. The weights are provided via an input array that we will call the convolution filter.

(i) Implement a CUDA kernel to compute 2D convolution for each element of an input 2D array by averaging the values of its neighboring elements.

(ii) Implement a CUDA kernel to compute 3D convolution for each element of an input 3D array by averaging the values of its neighboring elements in a cuboid of unit length keeping the element under consideration at the center.

• Use single-precision floating point type.

• Assume that the 2D and 3D arrays are squares and cubes. That is, sides have the same dimension and is a multiple of eight.

• The convolution filter will be a square with odd dimensions.

• Assume the missing boundary elements (i.e., ghost cells) are zero.

Implement two versions of the 2D and 3D kernels. The first one should be a basic version that uses global memory while the second one is your most optimized version that possibly exploits features like shared memory, constant memory, and loop tiling. Compare and report the performance improvement.
