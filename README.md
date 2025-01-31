# Ollama LM Studio Bridge
Use your Ollama managed models with LM Studio!

A utility script that fixes and enables LM Studio to use your Ollama models by creating the necessary symbolic links between Ollama's model storage and LM Studio's expected format.

## Notes from angrysky56: On Windows you can right click the file and open with gitbash if you have it installed and it will run automatically- the symlinks will register the models as double the space (boo!) so you probably don't want to leave the paths going to your main drive!!! They show up in the "default" folder at the top of the code so fill that in, it doesn't register the LM Studio custom folder right at least for me on Windows. But it does work- tested with Letta using LM Studio as the server and had access to the Ollama models.

## Prerequisites

- [Ollama](https://ollama.ai) installed with at least one model downloaded
  - (Please confirm by running `ollama list`)
- [LM Studio](https://lmstudio.ai) installed
- `jq` command-line JSON processor
  - macOS: `brew install jq`
  - Linux: `sudo apt-get install jq` or equivalent
  - Windows: `choco install jq`

## Installation

1. Clone the repository: `git clone https://github.com/eelbaz/ollama-lmstudio-bridge.git`
2. `cd ollama-lmstudio-bridge`
3. Make the script executable: `chmod +x ollama-lmstudio-bridge.sh`


## Usage

1. Run the script:
`./ollama-to-lmstudio-bridge.sh`

2. The script will:
   - Scan your Ollama models
   - Create the LM Studio models directory (`.lmstudio/models/lmstudio` on macOS/Linux, or equivalent on Windows)
   - Create symbolic links to your Ollama model files in the LM Studio models directory

3. In LM Studio:
   - Go to Settings
   - Set Models Directory to the path shown by the script (the script will display this path when it runs)
   - Your Ollama models should now appear in LM Studio from the dropdown

> **Note:** Every time you download a new model with Ollama, you'll need to re-run this script to sync the latest models to your LM Studio models folder.

## Supported Operating Systems

- macOS
- Linux
- Windows (requires Developer Mode or Administrator privileges for symlink creation)

## File Locations

- macOS/Linux:
  - Ollama manifests: `~/.ollama/models/manifests/registry.ollama.ai`
  - LM Studio models: `~/.lmstudio/models/lmstudio`

- Windows:
  - Ollama manifests: `%USERPROFILE%\AppData\Local\ollama\models\manifests\registry.ollama.ai`
  - LM Studio models: `%USERPROFILE%\Documents\.lmstudio\models\lmstudio`

## Troubleshooting

- **Symlink Creation Fails**: On Windows, enable Developer Mode or run as Administrator
- **Models Not Found**: Ensure you have downloaded models through Ollama first
- **jq Not Found**: Install jq using your system's package manager

## License

MIT License - See [LICENSE](LICENSE) file for details.
