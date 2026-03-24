# cross-stitch-patterns

🧶 **TapestryWeaver: Automated Crochet Pattern Generator**

TapestryWeaver is a Python-based CLI application designed to automate the creation of premium, grid-based crochet patterns (graphghans and tapestries) for the Etsy digital download market. By combining automated image processing with local AI orchestration, this tool allows creators to input a public-domain or licensed image, use natural language to overlay typography, and output a highly detailed, row-by-row PDF pattern formatted for immediate sale.

## 🚀 Business Overview

The Etsy crochet pattern market demands extreme clarity, visual aids, and foolproof mathematical precision. TapestryWeaver is built to service high-value, high-volume niches (such as alt-crochet, retro pop-culture, and cryptid tapestries) by generating mathematically perfect grid patterns and instructions.

This application eliminates the tedious manual labor of charting pixels and writing out row-by-row color counts, reducing pattern creation time from hours to minutes.

## ✨ Core Features

- **Automated Background Removal**: Isolates primary subjects from noisy backgrounds using programmatic alpha-layer stripping.
- **Natural Language Typography**: Accept simple text prompts to dynamically stamp chunky, readable text onto the image canvas at specified coordinates.
- **Yarn Color Quantization**: Maps image pixels strictly to predefined RGB palettes corresponding to commercial yarn brands (e.g., Lion Brand, Red Heart), capping patterns at 5-10 manageable colors.
- **Stitch-to-Pixel Downscaling**: Resizes the image to absolute stitch counts, ensuring 1 pixel equals 1 single crochet (SC) stitch.
- **Zero-Cost Local AI Orchestration**: Utilizes local LLMs to parse layout commands, handle math, and generate written instructions quietly in the background without incurring cloud API token costs.
- **Premium PDF Compilation**: Packages the reference image, the visual grid chart, and written row-by-row instructions into a branded, Etsy-ready PDF.

## 🛠️ Architecture and Tech Stack

The application is built around a headless, background-first philosophy, keeping the terminal clean and operating costs at absolute zero.

| Component          | Technology              | Purpose |
|--------------------|-------------------------|---------|
| CLI & Orchestration| Claude Code CLI         | Acts as the primary background orchestrator, quietly managing script execution and routing data between the AI and Python modules. |
| Local AI Engine    | Ollama                  | Powers the conversational interface and text generation completely locally, ensuring privacy and zero token costs. |
| Default Models     | DeepSeek, Qwen, Gemma 3 | Highly capable, lightweight models configured as the absolute defaults for parsing layout prompts and generating row-by-row instructions. |
| Image Processing   | Pillow (PIL) & numpy    | Handles typography stamping, canvas resizing, pixelation, and array mapping. |
| Subject Isolation  | rembg                   | Programmatically strips backgrounds from uploaded images. |
| Document Generation| ReportLab or FPDF       | Compiles the final visual charts and text instructions into a printable PDF. |

## ⚙️ The Processing Pipeline

The system operates in five distinct, automated stages once a prompt is issued.

1. **Command Parsing**: The user inputs an image and a natural language prompt via the CLI. The default Ollama model silently parses the string to extract text assets, stylistic choices, and X/Y spatial coordinates.
2. **Canvas Preparation**: The Python backend strips the image background using rembg. It then executes the typography script, stamping the extracted text onto the transparent canvas using thick, crochet-friendly fonts.
3. **Pixelation & Quantization**: The image is mathematically downscaled to match the requested blanket/tapestry dimensions (e.g., 150x200 pixels). Every pixel is then forced to snap to the nearest RGB value in the predefined commercial yarn palette.
4. **Instruction Generation**: The final pixel array is passed back to the local AI model. The model reads the array and generates perfect, human-readable written instructions (e.g., "Row 45: 10 Black, 5 White, 10 Black").
5. **Document Compilation**: The PDF library gathers the raw image, the pixelated visual grid, and the AI-generated written instructions, outputting a finalized `pattern_name.pdf` to the designated export folder.

## 💻 Example Usage

You interact with the system via simple, conversational commands in your terminal.

**Input:**
```
process image retro_skate.png --prompt "Center the text 'STAYIN ALIVE' horizontally across the bottom using a thick, blocky font. Limit the palette to 6 retro colors."
```

**Background Execution:** The CLI intercepts the command, routes the parsing to Gemma 3 or DeepSeek, executes the Python image processing scripts, reads the pixel array, writes the instructions, and compiles the document.

**Output:** `retro_skate_pattern.pdf` successfully generated in `/exports`.

Would you like me to draft the initial Python script for the Image Processing module (specifically the background removal and color quantization), or would you prefer to start by writing the configuration files to set up your local CLI environment?
