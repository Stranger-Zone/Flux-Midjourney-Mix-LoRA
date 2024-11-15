---
tags:
- text-to-image
- lora
- diffusers
- template:diffusion-lora
- Midjourney
- DallE
- Flux.1-Dev
- Realism
- Super-Realism
- Photo-Realism
- High-Fidelity
- Art-Mix
widget:
- text: >-
    midjourney mix, Shadow Projection, Captured from a close-up, eye-level
    perspective, a medium-sized boy with dark brown eyes and dark brown hair
    stands in front of a window. The boys face is angled slightly to the left,
    with a slight smile on his lips. His eyes are a piercing blue, and his
    eyebrows are a darker brown. His lips are a lighter shade of brown, and he
    is wearing a plaid shirt with a white collar. The background of the boy is
    blurred, and the boys shadow is cast on the window.
  output:
    url: images/mj12.png
- text: >-
    midjourney mix, Intense Red, a black cat is facing the left side of the
    frame. The cats head is tilted upward, with its eyes closed. Its whiskers
    are protruding from its mouth, adding a touch of warmth to the scene. The
    background is a vibrant red, creating a striking contrast with the cats fur.
  output:
    url: images/mj10.png
- text: ' midjourney mix, a close-up shot of a womans face, the womans hair is wet, and she is wearing a cream-colored sweater. The background is blurred, and there are red and white signs visible in the background. The womans eyebrows are wet, adding a touch of color to her face. Her lips are a vibrant shade of pink, and her eyes are a darker shade of brown.'
  output:
    url: images/mj4.png
base_model: black-forest-labs/FLUX.1-dev
instance_prompt: midjourney mix
license: creativeml-openrail-m
---
![strangerzonehf/Flux-Midjourney-Mix-LoRA](images/mjx.png)

<Gallery />

## Model Description Flux Midjourney Mix

Image Processing Parameters 

| Parameter                 | Value  | Parameter                 | Value  |
|---------------------------|--------|---------------------------|--------|
| LR Scheduler              | constant | Noise Offset              | 0.03   |
| Optimizer                 | AdamW  | Multires Noise Discount   | 0.1    |
| Network Dim               | 64     | Multires Noise Iterations | 10     |
| Network Alpha             | 32     | Repeat & Steps           | 35 & 4600|
| Epoch                     | 22  | Save Every N Epochs       | 1      |

    Labeling: florence2-en(natural language & English)
    
    Total Images Used for Training : 56 [ Hi -Res ]
    
## Best Dimensions

- 768 x 1024 (Best)
- 1024 x 1024 (Default)

## Setting Up
```python
import torch
from pipelines import DiffusionPipeline

base_model = "black-forest-labs/FLUX.1-dev"
pipe = DiffusionPipeline.from_pretrained(base_model, torch_dtype=torch.bfloat16)

lora_repo = "strangerzonehf/Flux-Midjourney-Mix-LoRA"
trigger_word = "midjourney mix"  
pipe.load_lora_weights(lora_repo)

device = torch.device("cuda")
pipe.to(device)
```
## Trigger words

> [!WARNING]
> **Trigger words:**  You should use `midjourney mix` to trigger the image generation.

## Sample Prompts

| **Prompt Name**           | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | **Settings**                                       |
|---------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------|
| **Woman with Denim Jacket** | A close-up shot of a woman with long brown hair in a bun, pulled back in a ponytail. She has blue eyes and pink lips, wearing a denim jacket with a front zipper. The background is blurred, out of focus.                                                                                                                                                                                                                                                                                                                                                                            | - Style: Midjourney Mix                                                                                                                                               |
| **Young Asian Woman**     | Close-up of a young Asian woman with long, wavy black hair against a white backdrop. She wears a white sleeveless bra with a tie at the neckline. Her hair cascades over her shoulders, adding texture. She has piercing blue eyes, pink lips, darker brown eyebrows, and lighter black hair, framing her face and cascading over her body. The backdrop is a stark white wall.                                                                                                                   | - Style: Midjourney Mix                                                                                                                                                |
| **Woman with Gold Necklace**  | Close-up of a woman's face captured in a low-angle shot. She has piercing blue eyes, vibrant brown hair, dark brown eyebrows, and deep red lips. She wears a gold necklace around her neck. Her hair is pulled back in a ponytail, framing her forehead. The backdrop is a light green wall with a window visible on the right side.                                                                                                           | - Style: Midjourney Mix                                                                                                                                               |
| **Woman in Cream Sweater** | Close-up shot of a woman's face with wet hair and eyebrows, wearing a cream-colored sweater. The background is blurred, with red and white signs visible. She has brown eyes, vibrant pink lips.                                                                                                                                                                                                                                                                                                                                                   | - Style: Midjourney Mix                                                                                                                                               |
| **Pixar-style Panda** | Ultra-detailed close-up of a panda's face styled like a Pixar or DreamWorks character. Features intricately textured fur for depth. The panda has a pirate eyepatch, with a roguish charm, a furrowed brow, and a smirking mouth. Emphasis on crisp details in facial features to bring out character’s personality. 3D render.                                                                                                  | - --v 6 --style raw --stylize 250 --ar 4:5          |
| **Korean Woman on Orange Backdrop** | Photography shot with an orange hue, featuring a Korean woman model against a solid orange backdrop, using a camera setup that mimics a large aperture, f/1.4.                                                                                                                           | - --ar 9:16 --style raw                                                                                                                                               |
| **Orange Bird Sculpture**  | A little bird made of a fresh orange that has been cut open, captured using photo-realistic techniques.                                                                                                                                                                                                                                                                                                                                                                                                    | - --ar 2:3 --stylize 400                                                                                                                                              |
| **Hot Pink Silhouette Portrait** | Profile silhouette of a woman against a vibrant hot pink backdrop. Focuses on the silhouette's edge using a camera setup with a large aperture to emphasize clarity. Low ISO preserves rich color. Photorealistic, UHD.                                                                            | - --ar 9:16 --chaos 1.7 --style raw                                                                                                                                   |
| **Japanese Girl Polaroid** | Close-up, high-quality photo portrait of an 18-21-year-old Japanese girl with brown hair, shot on a Polaroid camera. Features double eyelids.                                                                                                            | - --ar 34:65 --style raw                                                                                                                                              |
| **Black Cat on Red Background** | Intense red background featuring a black cat facing left. The cat's head is tilted upward with eyes closed and whiskers protruding, creating a warm contrast with the red background.                                                                                                                   | - Style: Midjourney Mix                                                                                                                                               |
| **Headshot of Young Man**  | Super realistic headshot of a handsome young man with brown hair, short beard, and a serious expression. Wears a dark gray sweater with buttons and a large shawl collar. Black background with soft studio lighting for portrait photography.                                                                                                                                                              | - --ar 85:128 --v 6.0 --style raw                                                                                                                                     |
| **Shadow Projection**      | Close-up, eye-level perspective of a medium-sized boy with dark brown eyes and hair, standing in front of a window. His face is angled slightly left, with a slight smile. Wears a plaid shirt with a white collar. His shadow is cast on the window.                                                                                          | - Style: Midjourney Mix                                                                                                                                               |

## Download model

Weights for this model are available in Safetensors format.

[Download](/strangerzonehf/Flux-Midjourney-Mix-LoRA/tree/main) them in the Files & versions tab.