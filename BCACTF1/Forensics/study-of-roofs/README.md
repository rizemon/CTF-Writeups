# study-of-roofs

My friend has always gotten in to weird things, and his recent obsession is with roofs. He sent me this picture recently, and said he hid something special in it. Do you think you could help me find it?

made by: @aidanglickman

File: dem_shingles.jpg

## Solution

![](./1.png)

Running ```binwalk``` showed that there was another JPEG in the file. If we run ```foremost```, 

![](./2.png)

We find out that there is another JPEG hidden in the file. Opening it reveals the flag.

![](./3.png)

Flag: ```bcactf{r4i53_7h3_r00f_liz4rd}``` 