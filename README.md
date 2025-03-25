# largefile

https://www.marqo.ai/blog/how-to-implement-local-rag-with-llama-3-2-and-marqo

https://www.linkedin.com/pulse/download-gguf-models-from-ollama-library-talles-carvalho-hn5vf/

llama-gguf-split --split-max-size 100M nomic-embed-text-v1.5.f16.gguf output_prefix--help

To split and combine a .gguf file on macOS, you can use the gguf-split utility included in llama.cpp to split the file into smaller parts and then use the cat command to combine them. 
Here's a breakdown:
1. Splitting the GGUF file:

    Install llama.cpp:
    If you haven't already, install llama.cpp which includes the gguf-split utility. 

Navigate to the directory:
Open your terminal and navigate to the directory where the .gguf file is located. 
Use gguf-split:
Run the following command, replacing path_to_your_gguf_file.gguf with the actual path to your file and output_prefix with a desired prefix for the split files:

Code

    ./gguf-split --split-max-size 1024M path_to_your_gguf_file.gguf output_prefix

    --split-max-size 1024M specifies the maximum size of each split file (1GB in this example). Adjust this value as needed. 

output_prefix will be the prefix for the split files (e.g., if you use my_model, the split files will be named my_model-00001-of-00005.gguf, my_model-00002-of-00005.gguf, etc.). 

2. Combining the GGUF parts:

    Navigate to the directory:
    Open your terminal and navigate to the directory where the split .gguf files are located. 

Use cat command:
Use the cat command to concatenate the split files, ensuring the files are in the correct order. The following command assumes that the first split file is named output_prefix-00001-of-00005.gguf and the last is output_prefix-00005-of-00005.gguf. Replace output_prefix with the actual prefix you used: 

Code

    cat output_prefix-00001-of-00005.gguf output_prefix-00002-of-00005.gguf output_prefix-00003-of-00005.gguf output_prefix-00004-of-00005.gguf output_prefix-00005-of-00005.gguf > combined_gguf_file.gguf

    Replace combined_gguf_file.gguf with the desired name for the combined file. 

Important Notes:

    File Naming:
    The gguf-split utility expects the split files to be named sequentially, with the format output_prefix-00001-of-00005.gguf, output_prefix-00002-of-00005.gguf, etc. 

Tools Support:
Many tools now support loading multi-part GGUF models directly, so you might not need to merge them at all. Check the documentation for the specific tool you are using. 
Alternatives:
You can also use other tools like 7-zip or similar to split and combine files, but gguf-split is designed specifically for GGUF files and is included in llama.cpp


brew install llama.cpp

llama-gguf-split --split-max-size 50M output_prefix--help-00002-of-00018.gguf output_prefix--help
