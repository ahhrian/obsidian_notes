### Step 1: Consolidation of Information
- The list of files generated from Prod are separated into tabs (based on their type - Cohort List, Aftercare, etc.)
- Consolidate the full list of files into 1 big Master.xlsx File
- Rename the tab with the full list of files to: ***Ingestion_files***
	- It should look something like this:
![[IngestionFiles_example.png]]

### Step 2: Add the Batch List Tab
- Recall that there is a ***Batch List*** tab in the Master.xlsx file provided in my zip folder
- Ensure that a similar ***Batch List*** tab exists in your newly generated file because this is the file that outlines how to split the big Master.xlsx file into the smaller batches you wanted
	- You can Copy-Paste the tab over into the new file to make it easier
>It looks like this:
![[BatchList_example.png|697]]

### Step 3: Editing the Batch List Tab
- The crucial columns in the file are **Order** and **Description**
- The **No of Files** column is used for extra verification, you can choose to leave the column blank if you don't know the exact number of files to be expected in each batch
	- If you do know the number, it's good to add it in because the script will validate whether it found the correct number of files by checking against this column
	- If the wrong number of files is found, it will skip writing that batching and output a warning log in the console, then you can check what's wrong

>"Description" Column
- This is the column that outlines the name of the files expected in each batch
- In the sample below, you'll notice that for Batch 2 & 3, file names may be repeated
- When Kenneth made this file, he repeated the named deliberately to reflect the number of versions that file has
	- E.g. Cohort List for ... JUL2025-OCT2025.xlsx has 4 versions in the Master tab
- The script however, only looks for unique file names in this column
	- i.e. As long as you name the file just once, it'll find ALL versions of that file in the Master Tab
- So, when you have the July & August 2026 files, you can add rows for each of them accordingly. If there's multiple versions of a file, just name it once

![[BatchList_repeated_names.png]]

>"Order" Column
- This column is what the script refers to when it writes the name of each batch file
	- The file names will follow this convention: ```  batch_{Order}_input.xslx ```
- So just ensure that the order of numbers in this column are correct, if not things may get messy

### Step 4: Preparing the Script
>File Path to read
- Now that the new Master.xlsx file is ready, add it into the directory with the script
	- In my version, the script exists in a ```/src``` folder with the Master.xlsx file outside that folder
- If you put both things in the same folder, remember to change the file path in the first cell of the script
	- The relative path is the first argument of the `read_excel()` function:
	  ![[read_excel_path.png]]
>Sheet names
- You'll notice the other two arguments are `sheet_name` (this dictates the *tab* in the excel file that is being read) 
- It's important to ensure your tab names are matching what is given as input here
	- If you happen to name the tabs differently, change the name provided in the argument accordingly
>Skiprows
- The `skiprows` argument exists only for Batch List as of now
	- This is because at the time that I made the script, July's batch was not ready
	- Those rows existed in the file, but had no file name provided in ***Description***
	- To avoid issues, I skipped the corresponding rows
	- Now that you'll have July's batch files by the time you use this script, you ***no longer*** need to skip those rows
- **NOTE**: If you copy the same Batch List tab over to your new Master file, your Batch List tab will have an empty blank row on top
	- If so, change the argument to `skiprows=1` (notice that the array of values is replaced by a single integer value)
	- If you happen to remove that empty top row in your new version, you can safely remove the `skiprows` argument completely
>Output Folder
- A quick final note, as I mentioned earlier, my files were arranged in the following format:
```
/yrsg_script_folder
	   |_ /src
		      |_ generate_ingestion_files.ipynb
	   |_ Master.xlsx
```
- In the final cell of the script, you'll notice that the path I've provided for the function to write the new files is the following:
  ![[to_excel_path.png]]
- This means the final folder arrangement would be:
```
/yrsg_script_folder
	   |_ /src
		      |_ generate_ingestion_files.ipynb
	   |_ Master.xlsx
	   |_ /ingestion_files
			  |_ batch_1_input.xlsx
			  |_ batch_2_input.xlsx
			  .
			  .
			  .
```
- If you happened to start off with Master.xlsx and the script being in the SAME directory, you may want to change the output path to:
  `/ingestion_files/....` (remove the `../` that precedes `/ingestion_files`) 
### Step 5: Run the Script :)
- Everything should be ready by now so just run each cell in the Jupyter Notebook and you should get a new folder named `/ingestion_files` with all the batch files :)


### Debugging Issues
- You'll see some logs in the console if a file has issues, just Claude your way through it if you run into those, I'm too lazy to write more than this oops . _ .