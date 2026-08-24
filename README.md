# CasualMobile2DComfyUI

The pipeline is designed to generate a batch of images in ComfyUI.

Necessary installation
1. ComfyUI Portable edition. Perform regular installation and run a localhost 
2. Ollama client. Perform a single prompt run to download a gemma4.26b thinking model.

Download necessary nodes in comfy from custom nodes manager
1. ComfyUI_IPAdapter_plus
2. rgthree-comfy
3. ComfyUI Impact Pack
4. ComfyUI-Custom-Scripts
5. Comfyroll Studio
6. comfyui-ollama
7. WAS Node Suite (Revised)
8. ComfyUI-OllamaGemini
9. ComfyUI-Openrouter_node

The pipeline uses a flux model and a LoRA model that is close to the style of the assignment images. The list bellow is additional downloads for the model to run. The downloaded files should be pasted in the installation paths
1. flux1-dev-fp8.safetensors - ComfyUI_windows_portable\ComfyUI\models\unet
https://huggingface.co/lllyasviel/flux1_dev/blob/main/flux1-dev-fp8.safetensors

2. clip_l.safetensors - ComfyUI_windows_portable\ComfyUI\models\clip
https://huggingface.co/comfyanonymous/flux_text_encoders/blob/main/clip_l.safetensors

3. t5xxl_fp8_e4m3fn.safetensors - ComfyUI_windows_portable\ComfyUI\models\clip
https://huggingface.co/calcuis/sd3.5-large-gguf/blob/main/t5xxl_fp8_e4m3fn.safetensors

4. SBG_quality_2_big.safetensors - ComfyUI_windows_portable\ComfyUI\models\loras
https://civitai.com/models/1685169/casual-game-art

5. ae.safetensors - ComfyUI_windows_portable\ComfyUI\models\vae
https://huggingface.co/lovis93/testllm/blob/ed9cf1af7465cebca4649157f118e331cf2a084f/ae.safetensors

6. 4x-UltraSharp - ComfyUI_windows_portable\ComfyUI\models\upscale_models
https://huggingface.co/lokCX/4x-Ultrasharp/blob/main/4x-UltraSharp.pth

After complete installation open the provided JSON file in Repo to run and if necessary customize the model. The model runs fully locally, so it is recommended to run the model on hardware with 12GB VRAM or 30GB~ spare RAM. Model can be additionally modified to run via using APIs by adding Gemini, OpenAI, Claude nodes, but those require separate API Key from the desired LLM and purchasing ComfyUI credits. 

Workflow
1. Locate "Theme input" node. Input the desired thematic setting for the cards. "Theme: Western". To make the item list generation slightly quicker list of items can be provided in brackets "(Cowboy hat, Antique Civil War Revolver, Cowboy boots, Tumbleweed, Sheriff badge, Tomahawk, Feather Whiskey bottle, Cactus, Wagon, Cartridge belt, High Noon, Sunset)", but the model can come up with a list on its own due to the main prompt.
2. The given prompt then goes into Ollama Generate node, where the main prompt will generate a list of items. 
3. The prompt then generates a list of ten items. The list is a string type text, which is later fed into the image generator. The list can be viewed in "Show Prompt Text" node. List example below:

The image is a 3D digital illustration of a magnifying glass, rendered in a casual mobile game asset style. The background is a vibrant, bright yellow graphic void featuring soft concentric circles radiating from the center to contrast sharply with the subject. In the center of the image, there is a magnifying glass with a thick black handle and a clear lens, crafted with chunky rounded 3D geometry and a smooth matte vinyl finish, suspended freely floating in mid-air with no floor underneath. The overall mood of the illustration is curious and observant.
The image is a 3D digital illustration of a fingerprint card, rendered in a casual mobile game asset style. The background is a bright, deep teal graphic void with a simple light ray pattern. In the center of the image, there is a white fingerprint card featuring a single black smudge, crafted with chunky rounded 3D geometry and a smooth matte vinyl finish, floating in mid-air with no floor underneath. The overall mood of the illustration is mysterious and analytical.
The image is a 3D digital illustration of a police badge, rendered in a casual mobile game asset style. The background is a vibrant, bright orange backdrop wall. In the center of the image, there is a shiny gold police badge with a star emblem, crafted with chunky rounded 3D geometry and a smooth matte vinyl finish, resting upright on a flat, smooth, solid-colored studio surface with zero floor texture. The surface and wall share a warm, saturated hue that makes the gold badge pop. The overall mood of the illustration is authoritative and official.
The image is a 3D digital illustration of an evidence bag, rendered in a casual mobile game asset style. The background is a vibrant, bright magenta backdrop wall. In the center of the image, there is a clear plastic-style evidence bag containing a small white powder, crafted with chunky rounded 3D geometry and a smooth matte vinyl finish, lying flat on its side on a flat, smooth, solid-colored studio surface with zero floor texture. The overall mood of the illustration is suspenseful and forensic.
The image is a 3D digital illustration of a case file, rendered in a casual mobile game asset style. The background is a vibrant, bright cyan backdrop wall. In the center of the image, there is a thick manila folder labeled "TOP SECRET", crafted with chunky rounded 3D geometry and a smooth matte vinyl finish, lying flat on its side on a flat, smooth, solid-colored studio surface with zero emblem and zero floor texture. The overall mood of the illustration is secretive and intense.
The image is a 3D digital illustration of a handheld flashlight, rendered in a casual mobile game asset style. The background is a vibrant, deep navy blue backdrop featuring a bright yellow radial sunburst pattern. In the center of the image, there is a heavy-duty black flashlight with chunky rounded 3D geometry and a smooth matte vinyl finish, lying flat on its side. The flashlight rests on a realistic, dark, weathered asphalt surface that completely covers the bottom section of the frame, hiding any background color underneath. The overall mood of the illustration is noir and atmospheric.
The image is a 3D digital illustration of a pair of handcuffs, rendered in a casual mobile game asset style. The background is a vibrant, bright red backdrop featuring white diagonal graphic stripes. In the center of the image, there is a matching pair of silver handcuffs with chunky rounded 3D geometry and a smooth matte vinyl finish, lying flat on their side. The handcuffs are placed on a realistic, cold grey concrete surface that completely covers the bottom section of the frame, hiding any background color underneath. The overall mood of the illustration is tense and captured.
The image is a 3D digital illustration of a vintage typewriter, rendered in a casual mobile game asset style. The background is a vibrant, bright green backdrop featuring a bold geometric pattern of circles. In the center of the image, there is a chunky black typewriter with round keys, crafted with chunky rounded 3D geometry and a smooth matte vinyl finish, resting upright. The typewriter stands on a realistic, dark polished mahogany wood surface with visible grain that completely covers the bottom section of the frame, hiding any background color underneath. The overall mood of a the illustration is classic and investigative.
The image is a 3D digital illustration of a detective's office, rendered in a casual mobile game asset style. The background is a rich, multi-layered scene of a dimly lit noir study with heavy shadows and light filtering through blinds. In the center of the image, there is a massive, grand evidence board covered in connected photos and strings, crafted with chunky rounded 3D geometry and a smooth matte vinyl finish, serving as the focal point. The scene includes a middle-ground desk and a background of dark bookshelves and a window. The overall mood of the illustration is mysterious and complex.
The image is a 3D digital illustration of a grand detective headquarters, rendered in a casual mobile game asset style. The background is a complete, cinematic environment of a large, bustling city precinct at night under a rainy sky. In the center of the image, there is a massive, iconic central trophy-like police station building with chunky rounded 3D geometry and a smooth matte vinyl finish, integrated into the urban landscape. The scene features foreground streetlights, middle-ground police vehicles, and a deep background of city skyscrapers and a glowing horizon. The overall mood of the illustration is epic and climactic.

4. Manual operation: The generation is autonomous, per each run the model generates a new list all the time. If the results are not satisfactory and you want to reuse the same list for generation disconnect "CR Prompt List" node from "Ollama Generate" node, and manually paste the desired amount strings from "Show Prompt Text" to "CR Prompt List".
5. The list of generated items goes through a CR Text Concatenate, which acts as a separator for all the strings. Also here is where you can connect and additional "text2" node, in which you can write down trigger words for your LoRA. In case of this model, the trigger word in "text2" is "SBG_quality"
6. The list then connects to the "Positive Prompt" node, which directly feeds the image generator the list of strings one by one. 
7. If you wish to add negative prompts then do so, by writing them in "Negative Prompt" node. 

Configuration
1. Choose diffusion model with "Load Diffusion Model". Here you can choose which model to use such as Krea2, Flux.
2. The "Load Diffusion Model" node connects to "Load LoRA (Model and CLIP)" node, which allows to choose LoRA models for your operation. 
3. Prompt string encoding is done using "Load CLIP (Dual)" node, specifically configured for flux diffusion model. If the model is changed so must be the encoders in "Load CLIP (Dual)" node. 
4. The processed images are fed to the "KSampler" node, here you can configure the generation parameters - steps, cfg, sampler, scheduler, denoise.
5. To choose the resolution of the output images change the desired values in "Empty Latent Image" node. From the same node you can choose the batch size, i.e. how many variant of 1 item image to make. The current setting is 10, meaning that after the generation is complete you'll get a 10 images per 10 items (100 overall)
6. The model uses a separate Upscaler. If neccessary, change it from "Load Upscale Model". During generation the upscaler makes copies of generated images with upscaled resolution and quality.

After the required configurations are complete, press the "Run" button to start the generation process. The model runs locally, therefore it is recommended to have a powerful enough system at hand. My hardware is: 
CPU - Ryzen 9 5900X
RAM - 64GB 
GPU - Nvidia 3070Ti with 8GB VRAM

Depending on the hardware the generation time can take up tp 25-35 minutes. 