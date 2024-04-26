# Hiring Challenge Solutions

Welcome to my repository for the MarbleAI Hiring Challenge. This repository includes a Google Colab notebook that contains my solutions to the given challenges, focusing on the given problem by using ControlNets along with StableDiffusion for achieving the end goal.

## Table of Contents

- [Opening the Notebook](#opening-the-notebook)
- [Features](#features)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Opening the Notebook

To access and interact with the notebook:

1. Open the notebook in Google Colab:
   - [Hiring Challenge Notebook](https://github.com/ChitranshS/HiringChallenge-1/blob/main/Hiring_Challenge_2.ipynb)
   - Click on the link to view the notebook directly in your browser.

2. To run the notebook:
   - Make sure you are logged into your Google account.
   - Click on `Copy to Drive` button at the top to save a copy of the notebook to your Google Drive.
   - You can now run and edit the notebook cells.
3. To run the inference on the images:
   - Clone the input_masks files from github and upload them to google collab under a new folder named upload
   - Start running the script
   - Make sure that the image uploaded by the user and the one mentioned below in the script are same.
   - 
## Product 1
![](https://github.com/ChitranshS/HiringChallenge-1/blob/main/cat_file.png)
![](https://github.com/ChitranshS/HiringChallenge-1/blob/main/variations.png)

## Product 2
![](https://github.com/ChitranshS/HiringChallenge-1/blob/main/product2.png)
![](https://github.com/ChitranshS/HiringChallenge-1/blob/main/Product2Variations.png)

## Product 3
![](https://github.com/ChitranshS/HiringChallenge-1/blob/main/Product3.png)
![](https://github.com/ChitranshS/HiringChallenge-1/blob/main/Product3Variations.png)

## Product 4
![](https://github.com/ChitranshS/HiringChallenge-1/blob/main/product4Variation/product4Variation.png)
![](https://github.com/ChitranshS/HiringChallenge-1/blob/main/product4.png)


## Product 5
![](https://github.com/ChitranshS/HiringChallenge-1/blob/main/product5.png)
![](https://github.com/ChitranshS/HiringChallenge-1/blob/main/Product5Variations.png)
![](https://github.com/ChitranshS/HiringChallenge-1/blob/main/Product5Variations1.png)


## Features

This notebook includes the following solutions and features:

- **CLIP Functionality**: I was planning to initially not use this but after a small test the results were drastically improved so I added CLIP to the preprocessing stage and got the word embeddings related to the product to preserve brand identity and product features that would be utilised later in the generation step.
- **Controlled Generation**: Here I am using ControlNet V1.1 along with Stable Diffusion 1.5 to get an controlled output by generating around the Mask that is preserved by this technique.The generation for the background is prompt-controlled. Other techniques such as image to image translation can be incorporated for using an studio-setup image as a reference.
  
- **Lighting Conditions**: As of now I am using the canny approach to preserve the dimensionality of the product image uploaded but I plan to use Normal Maps to preserve the lighting conditions in a more efficient manner.
  
- **Brand Identity** : Since I am preserving the input mask and generating around it in a controlled environment, the brand identity and the textual information is not much affected and is replicated in the final output.
  
- **Variational Angles** : I am planning to add Photogrammetry to the project which could generate the product images from every angle possible.Since we will have access to multiple angles then multiple backgrounds with varying elements and setups can be generated.
  
- **Shadows & Reflections** : The hard part are the reflections as they are basically information which in replicated on an generated surface with almost equal or less detail in the generation along with some noise/distortion to make it more believable.Regarding the shadows they are preserved again by the CLIP functionality and also I plan to incorporate the Depth Map of some images as well for testing.
  
- **Inference Time**: Using a T4-supported notebook in Colab, the entire image generation (5 sample images per input) process completes in under 3 minutes, significantly faster than the anticipated maximum of 10 minutes.

## Solution/Approach
I will be discussing the chain of thought I had on the problems statement the first time I read it and also what I was able to implement and how much was I able to achieve in this small span of 2 days.
### Initial Thoughts
- **1st step** : The user may upload any image of their liking meaning that we would required to segment the image to get the input image that we need to proceed ahead with. Using SAM by Meta or Mask-RCNN was my first thought but then I saw the sample inputs they were already easier to segment so I immediately skipped the segmentation part as it's easily managaeble.
- **2nd Step** : After we have access to the segmented image perform some detection and classify the object and perform some feature extraction which will make it easier to understand about the product and thus help in generating the AI-generated environment.
- **3rd Step** : To preserve the brand logo and identity use Specialised-OCR tools like tesseract or something else and further explore how to preserve this.
- **4th Step** : Finding techniques that can be utilized in performing the final act of the show. I found multiple techniques to perform the same task but each varying in it capabilities along with data and computation overheads.Some of them include textual inversion, outpainting and finally the winner ControlNets.
- **5th Step** : Understanding the requirements for the ControlNets and their applications with multiple models. Before finalising with Stable Diffusion 1.5 I researched on other models including OpenJourneyV4,DallEMini,DeepFloyd.
- **6th Step** :  I was also considering to explore latent diffusion as it also seems like a very similar technique with competent results but later I went ahead with SD1.5 due to time constraint on my half.
- **7th Step** : Enough research and architecture planning!! Now I started working on the pipeline and the steps that would be required to make this happen.
- 
### Final Thoughs before Submission
- **1st Step** : Came to know about CLIP and then proceeded with it and then got amazing results in preserving the product features and then had an idea about dynamic background spaces.
- **2nd Step** : Implemented CLIP and then the embeddings attained from it were used to understand the product better thus generate an environment better suited to it along with good repetition penalty to avoid similar ideas for the virtual product environment.
- **3rd Step** : Used open source models such as LLama-3-70b for generating prompts for dynamic environment generation i.e. using Llama-3 to generate better and creative prompts based on the CLIP information along with high temperature parameter to get more better ideas and prompts for background generation.
- **4th Step** : Using the dynamic prompts generated by Llama-3 to now generate the background for our product image using the ControlNets. Using canny to preserve the physical features of the product thus mimicking the exact dimensionality in generation which would later help in replacement by masking.
- **5th Step** : Using the mask of the intial product image and the new generated image to merge them together under one image.
- **6th Step** : Testing the entire process for a small batch of products and getting amazing results and impeccable time of generation well under 3 minutes provided we increase the creativity of the model. Under default settings the script performs the required taks well under two minutes.
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

Your Name - [Your email](mailto:chitransh0210@gmail.com)

Project Link: [https://github.com/ChitranshS/HiringChallenge-1](https://github.com/ChitranshS/HiringChallenge-1)
