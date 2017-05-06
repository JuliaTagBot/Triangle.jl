# TRIANGLE.jl

A tentative work to bind Jonathan Richard Shewchuk [Triangle](https://www.cs.cmu.edu/~quake/triangle.html) to Julia.

Note that while this binding-library is under a permissive license, the Triangle library isn't:
> Please note that although Triangle is freely available, it is copyrighted by the author and may not be sold or included in commercial products without a license.

So be wary of any possible conflict between your project license and Triangle's

## Installing

Just run `Pkg.add("https://github.com/furio/TRIANGLE.jl.git")` and `Pkg.build("TRIANGLE")`

### Windows

The build proces uses [VC++ for Python](https://www.microsoft.com/en-us/download/details.aspx?id=44266) to build so be sure you have it.

## API

After the usual `using TRIANGLE` you can use

`TRIANGLE.basic_triangulation(vertices::Array{Float64,2})` with:
* *vertices* containing the list of your vertices in the form of _[x1 y1; x2 y2; ... ; xn yn]_

Returns:
* Array{Array{Float64,2},1} an array of array of 3-vertices lists (a triangle). Each triangle is properly order in the whole mesh

`TRIANGLE.basic_triangulation(vertices::Array{Float64,2}, vertices_map::Array{Int64,1})` with: 
* *vertices* containing the list of your vertices in the form of _[x1 y1; x2 y2; ... ; xn yn]_ * *vertices_map* a list of custom integer identifier for the vertices

Returns:
* Array{Array{Float64,2},1} an array of array of 3-vertices lists (a triangle). Each triangle is properly order in the whole mesh

`TRIANGLE.constrained_triangulation(vertices::Array{Float64,2}, vertices_map::Array{Int64,1}, edges_list::Array{Int64,2})` with:
* *vertices* containing the list of your vertices in the form of _[x1 y1; x2 y2; ... ; xn yn]_ 
* *vertices_map* a list of custom integer identifier for the vertices
* *edges_list* a list of edges in the form of _[ vertex-identifier-1 vertex-identifier-2; vertex-identifier-1 vertex-identifier-3; ... ; vertex-identifier-N vertex-identifier-M ]_ that will be retaied during the constrained Delaunay triangulation

Returns:
* Array{Array{Float64,2},1} an array of array of 3-vertices lists (a triangle). Each triangle is properly order in the whole mesh
