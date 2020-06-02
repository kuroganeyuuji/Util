# Util
This Util library designed for some commn used functions in bee lab:

## installation
- Download
- pip install -r requirements.txt
- add this foldar path to you PYTHONPATH 

## Common Usage1:

For MRI users, you can use this util to read dicom data generated from 7T Bruker MRI, 


**Example**: after we export dicom datas from Bruker MRI, we save it to raw_data foldar,
````
+ raw_data
++++++ liu-20200212_liu-20200212_stell__**E15**_P1_2.16.756.5.5.100.3611282843.14246.1581486821.87
+++++++++++ MRIm1
+++++++++++ MRIm2
+++++++++++ MRIm3
`````
The below codes can read and show the images (in jupyter notebook).
```` python
from Util.os import readMRIfromIds
from Util.plot.staticPlot import *

rootDir = './raw_data/'
Images = readMRIfromIds(rootDir,[15])
plotMRIImage(Images[:,:,0],updown=False,axis=False)
````

## Common Usage2:
For TMS spfd users,you can visulize the coil and brain segementation file by:
````python
from Util.os.spfd import *

convSPFD = spfd()
convSPFD.visCoil("output_coil_vis","coil.csv","coil_position.txt")
# ouput vtk name will be output_coil_vis.vtu

dx,dy,dz = 1,1,1
convSPFD.visBrain("brain_map.csv",(dx,dy,dz))
# ouput vtk name will be brain_map_visBrain.vti
````
than you can confirm the coil position with brain in *Paraview*

After the simulation you can convert result.txt file to vector file like this:
````python
convSPFD.visJ(output_j_vtk_path,result_file_path)
````
