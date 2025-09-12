## Copy the code, change your i/o folders, and run it

```python
import os
import subprocess

input_folder = r"K:\Desktop\in" # <———————————— CHANGE TO YOUR PATHs
output_folder = r"K:\Desktop\out"

os.makedirs(output_folder, exist_ok=True)

for filename in os.listdir(input_folder):
    if filename.lower().endswith(".gif"):
        input_path = os.path.join(input_folder, filename)
        output_filename = os.path.splitext(filename)[0] + ".mp4"
        output_path = os.path.join(output_folder, output_filename)
        command = ["ffmpeg", "-y", "-i", input_path, "-c:v", "libx264", "-crf", "0", "-pix_fmt", "yuv420p", output_path]

        print(f"parsing: {filename} ——> {output_filename}")
        subprocess.run(command, stdout=subprocess.PIPE, stderr=subprocess.PIPE)

print("----------------\nBatch complete!!\n")
```
