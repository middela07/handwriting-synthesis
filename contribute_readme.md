# Analysis of Handwriting Synthesis Contribution

## Purpose:
This document will guide you through steps to contribute to the project, but it will be in vain due to better OCR execution alternatives. Read OCR_Alternative.txt to learn more.

### Why Contribute to sjvasquez/handwriting-synthesis?
I chose to contribute to this project specifically because (a) the project was well managed up to 2020, (b) the CONTRIBUTE section was the most detailed compared to other small-scale handwriting synthesis projects, and (c) the repository provided a demo representation of the current project. There is a possibility that the demo is the “ideal” output instead of the actual, but it still gives a tangible goal for the project. These are key qualities to look out for when choosing future projects too.

### Set-Up
To start, I installed Python and the PyCharm IDE. I followed a quick tutorial to clone the sjvasquaz/handwriting-synthesis project to my own git repository. Then, I copied my version of the project to my local server to edit the code files. Figures 3.1, 3.2, and 3.3 show this process. Any errors I got were minor, base-level issues with my own device, and the project worked completely up to this point.

3.1. Installing the PyTorch library on PyCharm IDE for Computer Vision
<img width="630" alt="Screen Shot 2023-04-20 at 2 34 32 AM" src="https://user-images.githubusercontent.com/51866569/233296058-750c6f7a-7cbf-47f5-9cfd-ad49f431a634.png">


3.2. From sjvasquaz, forked “handwriting-synthesis” repository successfully
<img width="787" alt="Screen Shot 2023-04-20 at 2 35 05 AM" src="https://user-images.githubusercontent.com/51866569/233296154-bdc61595-058a-4da0-8c59-2c1667108a5b.png">


3.3. Cloned “middela/07/handwriting-synthesis” repository to local server successfully
<img width="785" alt="Screen Shot 2023-04-20 at 2 35 20 AM" src="https://user-images.githubusercontent.com/51866569/233296240-1d4bfa0c-2115-4b0d-82da-577dc85160ae.png">



At this point, I can make changes to the exact files without impacting the main branch. Also, this is the start of the Proof of Concept, or a small demonstration of the project running to show that further changes/contributions to the project are possible. However, as you read, you will see how this project can fail on one’s device because of the Python configurations.

### Preparing the Data
The next step is to prepare the data, which is seen in the instructions in Figure 3.4. The prepare_data.py file will not run unless certain libraries are installed, all of which are listed in the requirements.txt file. Installing all but tensorflow 1.6 will allow prepare_data.py to run. Figure 3.5 is an example of the missing library error, which can be resolved by installing the module for the project.

3.4. Instructions in README to prepare data.   
<img width="485" alt="Screen Shot 2023-04-20 at 2 35 37 AM" src="https://user-images.githubusercontent.com/51866569/233296318-1bdf1bca-212b-481a-a463-e37eefcd9052.png">


3.5. Various requirements need to be fulfilled before preparing data, such as matplotlib installation. 
<img width="788" alt="Screen Shot 2023-04-20 at 2 35 49 AM" src="https://user-images.githubusercontent.com/51866569/233296457-d18ae573-d854-449f-852d-a2bea0194910.png">


3.6. List of requirements: All except tensorflow fulfilled are necessary to prepare data   
<img width="397" alt="Screen Shot 2023-04-20 at 2 36 00 AM" src="https://user-images.githubusercontent.com/51866569/233296513-f7e0cf05-f1ad-4914-83b8-114bc3d218d5.png">



Even before uploading the data, I needed faced errors, such as needing to import the ‘matplotlib’ library in order to support the model, pictured in Figure 3.5. It was helpful that this project contained a file that listed all of the libraries used in this project so I could understand the source of any errors (Figure 3.6). Most of the bugs were caused by needing to import the right library. All of the libraries, except tensorflow, were correctly imported and were sufficient enough to \ prepare the data files.

3.7. Find & download data files  
<img width="347" alt="Screen Shot 2023-04-20 at 2 36 29 AM" src="https://user-images.githubusercontent.com/51866569/233296687-43951825-8a65-42e7-a890-974db402c72d.png">



The Model Training Instructions state that running all of the data will take “several days” on an advanced Tesla GPU. Because of typical time constraints to train with rnn.py (and for proof-of-concept demonstration purposes), I downloaded a small subset of the IAM Online Handwriting Dataset (https://fki.tic.heia-fr.ch/databases/iam-on-line-handwriting-database). I used only the ASCII folder shown in Figure 3.7 for now.

3.8. Data extraction & preparation, successfully  
<img width="373" alt="Screen Shot 2023-04-20 at 2 36 51 AM" src="https://user-images.githubusercontent.com/51866569/233295914-4481ee92-0544-4077-8f33-ca8d75dd3918.png">



### Training Model with Data

At this point, the data is properly prepared, and all files used are listed in Figure 3.8. The READ ME then instructs to “run rnn.py,” where the error in Figure 3.9 pops up, prompting to import a module named tensorflow. This can seemingly be resolved when importing module tensorflow 2.12, until rnn.py still fails to run, claiming that the tensorflow requirement is not fulfilled, due to the fact that the program needs tensorflow version 1.6.

3.9. Run rnn.py unsuccessful because import tensorflow was not fulfilled   
<img width="303" alt="Screen Shot 2023-04-20 at 2 37 09 AM" src="https://user-images.githubusercontent.com/51866569/233295489-a4f840d1-b1bd-4546-a440-6488887766a1.png">



3.10. Attempt to import tensorflow 1.6 unsuccessful because tensorflow 1.6 is not supported by Python version 3.9.6 
<img width="718" alt="Screen Shot 2023-04-20 at 2 37 25 AM" src="https://user-images.githubusercontent.com/51866569/233296803-3802e891-4a3f-4952-9396-5df701d1aaf4.png">



Downgrading tensorflow should be an easy fix, yet the final error message shows that the newest Python version (3.9.6) isn’t configured to use a tensorflow version below 2.8.0rc1 (Figure 3.10). Even then, only Python version 3.4-3.6 is viable to downgrade to (Figure 3.11).
In this case, the user would be required to downgrade Python to a much older version. 

3.11. TensorFlow-1.6.0 is only supported by Python version 2.7, 3.3-3.6.  
<img width="725" alt="Screen Shot 2023-04-20 at 2 37 45 AM" src="https://user-images.githubusercontent.com/51866569/233296840-7b553e7a-4788-4fa8-a225-a07f93dec552.png">




### Alternatives
At this point, there are several options: downgrade Python to an older version to continue to contribute, find a different way to contribute to this project, find an alternative project, or contribute a different way. Downgrading Python is not difficult, but should a large-scale AI company backtrack on the latest technology to accommodate one module (tensorflow) when the tech world will only be moving forward, or should they find a new way to implement Handwriting Synthesis another way? Probably not.

### Final Thoughts
Supported by a concept called tech debt, which is explored in the OCR_Alternative.txt, a better way to use OCR/Handwriting Synthesis is to avoid contributing to this project altogether and use a method better suited for today’s evolving technologies. Attempting to contribute to this project provides novice AI engineers with industry practice and debugging familiarity, but it also helps the coder make smart, knowledgeable decisions about implementing even slightly outdated projects for long-scale AI investment. I thank my mentor for her guidance to learn about Open Source Contribution to Computer Vision throughout this project.


