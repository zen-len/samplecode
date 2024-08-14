# This script monitors a specified folder for new .fil files and processes them by modifying specific content 
# and saving the output to a new file in a designated output folder.

# 1. Folder Paths Setup:
#    - $inputFolderPath: The path to the folder being monitored for new files.
#    - $outputFolderPath: The path to the folder where processed files will be saved.

# 2. File System Watcher Initialization:
#    - A FileSystemWatcher object ($watcher) is created to monitor the input folder ($inputFolderPath) for any new .fil files.
#    - The watcher is configured to exclude subdirectories and start monitoring events immediately.

# 3. Queue Creation:
#    - A queue ($queue) is created to manage the files detected by the watcher that need to be processed.

# 4. Event Registration:
#    - An event handler is registered to handle the "Created" event, which is triggered when a new .fil file 
#      is created in the input folder.
#    - When a new file is detected, its path is added to the queue for processing.

# 5. File Processing Function (ProcessFile):
#    - The script defines a function ProcessFile that takes the path of an input file, processes it, and saves the 
#      output to a new file in the output folder.
#    - Processing Details:
#      - The content of the input file is read line by line.
#      - If a line has 132 or more characters:
#        - It extracts a substring from the 7th column (positions 106 to 112) and removes the first two characters.
#        - It then replaces a substring in the 2nd column (positions 31 to 35) with this adjusted value.
#      - The modified lines are stored in an array and then written to the output file in the output folder.

# 6. Continuous Monitoring and Processing Loop:
#    - The script enters an infinite loop where it continuously checks if there are files in the queue.
#    - If the queue is not empty, the script dequeues the next file and processes it using the ProcessFile function.
#    - If there are no files to process, the script pauses for 5 seconds to avoid high CPU usage.

# 7. Output and Error Handling:
#    - The script logs the processing status to the console, indicating the files that have been processed.
#    - If an error occurs during file processing, it logs the error to the console.

# The script runs continuously until manually stopped (e.g., by pressing Ctrl+C).
