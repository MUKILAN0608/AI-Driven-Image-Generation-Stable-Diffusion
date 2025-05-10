# 🎨 Stable Diffusion Custom Image Generator

A professional AI-powered text-to-image generation tool using the **Stable Diffusion model**. This project allows users to create high-quality, AI-generated images by customizing prompt text, guidance scale, inference steps, and the number of images to generate. Ideal for creatives, developers, and research scholars exploring generative AI.

---

## 📌 Features

- 📝 **Text-to-Image Generation** using Stable Diffusion.
- 🎛️ User inputs for:
  - Prompt text
  - Guidance scale
  - Inference steps
  - Number of images
- ⚡ GPU-accelerated generation via `torch.float16`.
- 🖼️ Image display and automatic saving.
- 📊 Research-ready and easily extendable.

---

## 📦 Installation

1️⃣ Clone this repository:

```bash
git clone https://github.com/MUKILAN0608/stable-diffusion-custom-image-generator.git
cd stable-diffusion-custom-image-generator
```
🚀 Usage
Run the following code in a Python or Colab environment:


from diffusers import StableDiffusionPipeline
import torch
from PIL import Image
from IPython.display import display

# Load the Stable Diffusion model
pipe = StableDiffusionPipeline.from_pretrained(
    "runwayml/stable-diffusion-v1-5",
    torch_dtype=torch.float16
).to("cuda")

# User inputs
prompt = input("Enter your image prompt: ")
guidance_scale = float(input("Enter guidance scale (e.g. 7.5): "))
num_inference_steps = int(input("Enter number of inference steps (e.g. 50): "))
num_images = int(input("Enter number of images to generate: "))

# Generate and display images
with torch.autocast("cuda"):
    for i in range(num_images):
        image = pipe(
            prompt, 
            guidance_scale=guidance_scale, 
            num_inference_steps=num_inference_steps
        ).images[0]
        display(image)
        image.save(f"generated_image_{i+1}.png")


📖 Sample Input

Enter your image prompt: A futuristic neon-lit cyberpunk cityscape with flying cars  
Enter guidance scale (e.g. 7.5): 8.0  
Enter number of inference steps (e.g. 50): 40  
Enter number of images to generate: 2
📊 Future Scope & Research Potential
This project opens doors for multiple research directions:

Prompt engineering impact on image fidelity.

Inference time vs image quality trade-offs.

Comparative studies with other text-to-image diffusion models.

Generation of large synthetic image datasets for supervised vision models.

Integration with web frontends (Gradio, Streamlit) for public-facing AI tools.

Exploring text-guided image upscaling models.

Benchmarking on different GPU architectures.

📑 License
This project is licensed under the MIT License.

✨ Acknowledgments
RunwayML Stable Diffusion v1.5

Hugging Face Diffusers Library
