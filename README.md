# Hiring Challenge Solutions

Welcome to my repository for the MarbleAI Hiring Challenge. This repository includes a Google Colab notebook that contains my solutions to the given challenges, focusing on the given problem by using ControlNets along with StableDiffusion for achieving the end goal.
# TL;DR (Ai-Generated)
- **Repository Purpose**: Solutions for MarbleAI Hiring Challenge.
- **Approach Highlights**:
    - Utilized ControlNets and StableDiffusion.
    - Integrated CLIP for improved results.
    - Focused on controlled generation and lighting preservation.
    - Retained brand identity.
    - Planned for multiple angle generation.
- **Features**:
    - CLIP Functionality.
    - Controlled Generation.
    - Lighting Conditions Preservation.
    - Brand Identity Retention.
    - Variational Angles and Multiple Angles.
    - Shadows & Reflections Handling.
- **Inference Time**: Under 3 minutes using T4-supported notebook in Colab.
- **Solution Development**:
    - Initial Thoughts included segmentation and object classification.
    - Final Approach incorporated CLIP, dynamic background generation, and ControlNets.
## Table of Contents

- [Opening the Notebook](#opening-the-notebook)
- [Features](#features)
- [Results](#results)
   - [First Iteration of Approach](#first-iteration-of-approach)
   - [Second Iteration of Approach](#second-iteration-of-approach)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Opening the Notebook

To access and interact with the notebook:

1. Open the notebook in Google Colab:
   - [Hiring Challenge Notebook](https://github.com/ChitranshS/HiringChallenge-1/blob/main/Hiring_Challenge_Final_version.ipynb)
   - Click on the link to view the notebook directly in your browser.

2. To run the notebook:
   - Make sure you are logged into your Google account.
   - Click on `Copy to Drive` button at the top to save a copy of the notebook to your Google Drive.
   - You can now run and edit the notebook cells.
3. To run the inference on the images:
   - Connect to a T4 instance and then follow the instructions mentioned in the notebook
   - Start running the script
   - **There would be some user-controlled parameters so please read it through**
  
## Features

This notebook includes the following solutions and features:

- **CLIP Functionality** _(Image-text-extraction)_: I was planning to initially not use this but after a small test the results were drastically improved so I added CLIP to the preprocessing stage and got the word embeddings related to the product to preserve brand identity and product features that would be utilised later in the generation step.
  
- **Controlled Generation**: Here I am using ControlNet V1.1 along with Stable Diffusion 1.5 to get an controlled output by generating around the Mask that is preserved by this technique.The generation for the background is prompt-controlled. Other techniques such as image to image translation can be incorporated for using an studio-setup image as a reference.
  
- **Lighting Conditions**: As of now I am using the canny approach and histogram equalization to preserve the dimensionality of the product image uploaded but I plan to use Normal Maps to preserve the lighting conditions in a more efficient manner.
  
- **Brand Identity** : Since I am preserving the input mask and generating around it in a controlled environment, the brand identity and the textual information is not much affected and is replicated in the final output.
  
- **Variational Angles** : I am planning to add Photogrammetry to the project which could generate the product images from every angle possible.Since we will have access to multiple angles then multiple backgrounds with varying elements and setups can be generated.

- **Multiple Angles** : This is basically a feature wherein we can get the product image in various enviroments and using 2d augmentation techniques to generate new data points. 
  
- **Shadows & Reflections** : The hard part are the reflections as they are basically information which in replicated on an generated surface with almost equal or less detail in the generation along with some noise/distortion to make it more believable.Regarding the shadows they are preserved again by the CLIP functionality and also I plan to incorporate the Depth Map of some images as well for testing.
  
- **Inference Time**: Using a T4-supported notebook in Colab, the entire image generation (5 sample images per input) process completes in under 3 minutes, significantly faster than the anticipated maximum of 10 minutes.

# Results
## First Iteration of Approach
### Product 1
<div>
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/cat_file.png" width=30% height=30%>
<img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/variations.png" width=60% height=60%>
</div>

### Product 2
<div>
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/product2.png" width=30% height=30%>
<img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/Product2Variations.png" width=60% height=60%>
</div>

### Product 3
<div>
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/Product3.png" width=30% height=30%>
<img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/Product3Variations.png" width=60% height=60%>
</div>

### Product 4

<div >
<img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/product4Variation/product4Variation.png" width=30% height=30%>
<img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/product4.png" width=60% height=60%>
</div>

### Product 5
<div>
<img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/product5.png" width=30% height=30%>
<img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/Product5Variations.png" width=60% height=60%>
</div>



# Second Iteration of Approach
### Product A
<div>

   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/camera-2.png" width=100% height=100%>
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/camera-6.png" width=100% height=100%>
   
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/camera-5.png" width=100% height=100%>
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/camera-7.png" width=100% height=100%>

</div>

### Product B
<div>
      <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/lotion-2.png" width=100% height=100%>
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/lotion-5.png" width=100% height=100%>
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/lotion-3.png" width=100% height=100%>
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/lotion-4.png" width=100% height=100%>
</div>

### Product C (Mouse on my table)
<div>
     <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/mouse-3.png" width=100% height=100%>
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/mouse-5.png" width=100% height=100%>
</div>

### Product D

<div >
 <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/ring-6.png" width=100% height=100%>
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/ring-5.png" width=100% height=100%>
   
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/ring-3.png" width=100% height=100%>
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/ring-7.png" width=100% height=100%>
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/ring-8.png" width=100% height=100%>

</div>

### Product E
<div>
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/soap-1.png" width=100% height=100%>
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/soap-2.png" width=100% height=100%>
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/soap-5.png" width=100% height=100%>
</div>

### Product F
<div>
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/shoes-1.png" width=100% height=100%>
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/shoes-4.png" width=100% height=100%>
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/shoes-5.png" width=100% height=100%>
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/shoes-3.png" width=100% height=100%>

</div>

### Product G
<div>
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/shaker-2.png" width=100% height=100%>
   <img src ="https://github.com/ChitranshS/HiringChallenge-1/blob/main/assets/images/shaker-4.png" width=100% height=100%>

</div>

## Solution/Approach
I will be discussing the chain of thought I had on the problems statement the first time I read it and also what I was able to implement and how much was I able to achieve in this small span of 2 days.
### Initial Thoughts (**You may skip the initial thoughts to see the final approach**)

- **1st step** : The user may upload any image of their liking meaning that we would required to segment the image to get the input image that we need to proceed ahead with. Using SAM by Meta or Mask-RCNN was my first thought but then I saw the sample inputs they were already easier to segment so I immediately skipped the segmentation part as it's easily managaeble.
- **2nd Step** : After we have access to the segmented image perform some detection and classify the object and perform some feature extraction which will make it easier to understand about the product and thus help in generating the AI-generated environment.
- **3rd Step** : To preserve the brand logo and identity use Specialised-OCR tools like tesseract or something else and further explore how to preserve this.
- **4th Step** : Finding techniques that can be utilized in performing the final act of the show. I found multiple techniques to perform the same task but each varying in it capabilities along with data and computation overheads.Some of them include textual inversion, outpainting and finally the winner ControlNets.
- **5th Step** : Understanding the requirements for the ControlNets and their applications with multiple models. Before finalising with Stable Diffusion 1.5 I researched on other models including OpenJourneyV4,DallEMini,DeepFloyd.
- **6th Step** :  I was also considering to explore latent diffusion as it also seems like a very similar technique with competent results but later I went ahead with SD1.5 due to time constraint on my half.
- **7th Step** : Enough research and architecture planning!! Now I started working on the pipeline and the steps that would be required to make this happen.
  
### Final Thoughs before Submission
- **1st Step** : Came to know about CLIP and then proceeded with it and then got amazing results in preserving the product features and then had an idea about dynamic background spaces.
- **2nd Step** : Implemented CLIP and then the embeddings attained from it were used to understand the product better thus generate an environment better suited to it along with good repetition penalty to avoid similar ideas for the virtual product environment.
- **3rd Step** : Used open source models such as LLama-3-70b for generating prompts for dynamic environment generation i.e. using Llama-3 to generate better and creative prompts based on the CLIP information along with high temperature parameter to get more better ideas and prompts for background generation.
- **4th Step** : Using the dynamic prompts generated by Llama-3 to now generate the background for our product image using the ControlNets. Using canny to preserve the physical features of the product thus mimicking the exact dimensionality in generation which would later help in replacement by masking.
- **5th Step** : Using the mask of the intial product image and the new generated image to merge them together under one image.
- **6th Step** : Resizing the mask to match the dimension of the generated image.
- **7th Step** : Testing the entire process for a small batch of products and getting results of generation well under 4 minutes provided we increase the creativity of the model. Under default settings the script performs the required taks well under two minutes.
## Contributing

If you have suggestions to improve this notebook, your contributions are welcome! Follow these steps:

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

Chitransh Srivastava - [chitransh0210@gmail.com](mailto:chitransh0210@gmail.com)

Project Link: [https://github.com/ChitranshS/HiringChallenge-1](https://github.com/ChitranshS/HiringChallenge-1)
