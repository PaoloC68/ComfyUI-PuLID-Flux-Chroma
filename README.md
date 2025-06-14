# ComfyUI-PuLID-Flux-Chroma

🎨 **The first PuLID implementation with full Chroma model support for ComfyUI!**

Face-consistent character generation using PuLID (Pure and Lightning ID) with both FLUX and Chroma models in ComfyUI.

## 🌟 Key Features

- **Full Chroma Compatibility**: First working implementation of PuLID with Chroma guidance
- **Dual Model Support**: Works seamlessly with both standard FLUX and Chroma models
- **Automatic Model Detection**: Intelligently switches between FLUX and Chroma implementations
- **Face Identity Preservation**: Maintains consistent character faces across generations
- **AMD GPU Optimized**: Tested and optimized for AMD RX 6900 XT (16GB VRAM)

## 🚀 What's New

### Chroma Model Support
This fork introduces groundbreaking Chroma model compatibility, allowing you to use PuLID's powerful face identity preservation with Chroma's enhanced detail and artistic capabilities.

**Tested with**: chroma-unlocked-v35-detail-calibrated_float8_e4m3fn_scaled_stochastic.safetensors

### Technical Improvements
- Resolved dtype compatibility issues between BFloat16/Half precision
- Implemented Chroma's custom modulation system
- Fixed missing `time_in` attribute in Chroma models
- Comprehensive dtype conversion throughout the pipeline

See [CHANGELOG.md](CHANGELOG.md) for detailed technical achievements.

## 📦 Installation

1. Navigate to your ComfyUI custom nodes directory:
   ```bash
   cd ComfyUI/custom_nodes
   ```

2. Clone this repository:
   ```bash
   git clone https://github.com/[your-username]/ComfyUI-PuLID-Flux-Chroma.git
   ```

3. Install requirements:
   ```bash
   cd ComfyUI-PuLID-Flux-Chroma
   pip install -r requirements.txt
   ```

4. Download the PuLID model:
   - Download `pulid_flux_v0.9.1.safetensors` (1.06GB)
   - Place it in `ComfyUI/models/pulid/`

## 🎮 Usage

### Basic Workflow
1. Load your Chroma or FLUX model as usual
2. Add the "Apply PuLID Flux" node
3. Connect your reference face image(s)
4. The node automatically detects and adapts to your model type

### Example Workflows
- `chroma_pulid_test.json` - Basic Chroma + PuLID workflow
- `flux_pulid_multi.json` - Multi-face FLUX workflow  
- `pulid_flux_16bit_simple.json` - Simple 16-bit precision workflow

### Optimal Settings for Chroma
- Resolution: 768x768
- Steps: 26 (Chroma's optimal)
- PuLID weight: 0.9-1.0
- Sampler: Euler Simple or Euler Beta

## 🔧 Advanced Features

All original PuLID-Flux-Enhanced features are preserved:

### Fusion Methods
- **mean** (official) - Balanced fusion of multiple faces
- **concat** - Concatenate embeddings
- **max/max_token** - Emphasize dominant features
- **train_weight** - Novel fast embedding self-training

### Additional Options
- RGB/Gray image toggle
- Prior image support for guided training
- Multi-image input with various fusion strategies

## 💡 Tips for Best Results

1. **Image Quality**: Use high-quality reference images with clear faces
2. **Image Size**: 1512x1512 reference images work well (avoid 4K+ images)
3. **PuLID Weight**: 0.9-1.0 for v0.9.1 model
4. **Precision**: fp16 recommended, fp8 acceptable, avoid gguf/nf4

## 🙏 Credits

This project builds upon the excellent work of:
- Original PuLID-Flux implementation by [@balazik](https://github.com/balazik/ComfyUI-PuLID-Flux)
- PuLID-Flux-Enhanced by [@sipie800](https://github.com/sipie800/ComfyUI-PuLID-Flux-Enhanced)
- PuLID paper authors and researchers

Special thanks to the Chroma community for inspiration and testing.

## 📝 License

This project inherits the original MIT License. See [LICENSE](LICENSE) for details.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

## ⚠️ Note

This is an experimental implementation. While it works reliably with tested models, results may vary with different Chroma variants or custom FLUX fine-tunes.