# features_extractor_3Dstepfile
Extract features from a technical definition as *.step 3D model  

One [3d_model.step](./samples/sample1.step) document is used to generate a vector of N features.  

This features extractor is used a preliminary step to feed a machine learning model described [here](https://github.com/BruSunshine/predict_manufacturing_costs/blob/main/README.md)  

**Format**  

This files is a step \*.stp or \*.step format described in https://en.wikipedia.org/wiki/ISO_10303-21#DATA_section    

**Comment**  

Each part is linked to its 3D model, stored as a step file, and named in a way similar to the pdf 2D drawing.   
The step files can be opened with a text editor or with CAD software.  

Preprocessing of step files aims at generating a dataframe of features for each step file.  
We made the choice to use an open source CAD software called FreeCAD with a good integration of pythons macros and a good community of users.  
This software can be operated with or without GUI from a jupyter notebook and we found it usefull for extracting the topological features from the step file.  

FreeCAD library is used to extract the features. FreeCAD GUI is used in combination to the FreeCAD App to help visual cross-checking when needed.  

List of features extracted which we expect having impact on the part complexity and finally on the part costs:  

Solids
 - Number of solids

Following parameters understood as sums on all solids:  

Edges  
 - Number of edges  
 - Lenght per Curve types
 - Lenght per Curve types / Total lenght of edges
 - Total lenght of edges
 - Describe Edges lenght values

Faces  
 - Number of faces
 - Area per Surface types
 - Volume per Surface types
 - Area per Surface types / Total area of faces
 - Volume per Surface types / Total volume of faces
 - Total area of faces
 - Total volume of faces
 - Describe Faces area values

Volumes and bounding box  
 - Volume of the part
 - Volume of the bounding box
 - Volume of the part / Volume of the bounding box
 - bounding box diag
 - bounding box X
 - bounding box Y
 - bounding box Z
 - Polynomial features of X,Y,Z

Holes drillings:  
 - Number of holes
 - Diameters: mini maxi average
 - Volume of drillings
 - Number of different diameters
