# Image-encoding-from-scalars
Adding channel information to the scalar vector for image encoding using scalarmappable class

# Problem Definition

Recently, I have been working on biometric identification using footstep pressure measured from floor mounted mat. The mat measures the Ground Reaction Force when the foot is in contact with the measuring sensors. In order to extract the foot print of the foot step it is essential to represent the data spatially. 

Using the GRF values from the sensors and the information of the sensor arrangements in the pressure mat, a 2D matrix is formed which represents the spatial arrangements of the sensors and its respective pressure values. To make the representation more efficient, the pressure values can be distinguished by different colors and the foot print matrix can be considered as a footsteps.

**Distribution of pressure values**

![image](https://user-images.githubusercontent.com/44360746/64935114-b294fc80-d881-11e9-80cd-11c83c2ad0bf.png)


After encoding the pressure values to image pixel values (0-255), the 2d matrix is converted to single channel image matrix. 

**Image Results**

![image](https://user-images.githubusercontent.com/44360746/64935196-66968780-d882-11e9-9ff3-a97310030e38.png)


The resulting image lacks the channel information in the matrix as the channel information provides much more efficient spatial representation of an image.

# Solution

Using Scalarmappable class in matplotlib, it is possible to add channel information to encode a vector to its equivalent 3 channel image representation.


		Bases: object

	class to support scalar data to RGBA mapping. The ScalarMappable makes use of data normalization before returning RGBA colors from the 	 given colormap.

	Parameters:	
	norm : matplotlib.colors.Normalize instance
	The normalizing object which scales data, typically into the interval [0, 1]. If None, norm defaults to a colors.Normalize object     	which initializes its scaling based on the first data processed.

	cmap : str or Colormap instance
	The colormap used to map normalized data values to RGBA colors.
	
It convert from a floating point value to a colour in a two step process. First the floating point number is mapped to the range 0..1, then the the appropriate RGB for that normalised number is looked up in the colour map.

**Results**

![image](https://user-images.githubusercontent.com/44360746/64935420-bf1a5480-d883-11e9-877a-e22d658c2bc6.png)


