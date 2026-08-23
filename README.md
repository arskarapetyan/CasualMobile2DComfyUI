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

After complete installation open the provided JSON file in Repo to run and if necessary customize the model. The model runs fully locally, so it is recommended to run the model on hardware with 12GB VRAM or 30GB~ spare RAM. Model can be additionally modified to run via using APIs by adding Gemini, OpenAI, Claude nodes, but those require separate API Key from the desired LLM and purchasing ComfyUI credits. 

Workflow
1. Locate "Theme input" node. Input the desired thematic setting for the cards. "Theme: Western". To make the item list generation slightly quicker list of items can be provided in brackets "(Cowboy hat, Antique Civil War Revolver, Cowboy boots, Tumbleweed, Sheriff badge, Tomahawk, Feather Whiskey bottle, Cactus, Wagon, Cartridge belt, High Noon, Sunset)", but the model can come up with a list on its own due to the main prompt.
2. 