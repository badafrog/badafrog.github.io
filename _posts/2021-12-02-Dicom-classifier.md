---
layout: post
title: Dicom Classifier
subtitle: File classification using python & multiprocessing
categories: work
tags: [python, work]
---

* Code written in summer 2021

### What is a DICOM file?

A DICOM file is an image saved in the **Digital Imaging and Communications in Medicine**(DICOM) format.
It contains an image from a medical scan, such as an ultrasound or MRI. 
DICOM files may also include identification data for patients to link the image to a specific individual.
- fileinfo.com

### Classification

**File directory tree of Unclassified dicom files:**

Unclassified_folder
├─patient_1
│  ├─.dcm
│  ├─.dcm
│  ⋮
│  └─dicom_n.dcm
├─patient_2
│  ├─.dcm
│  ├─.dcm
│  ⋮
│  └─.dcm
⋮
└─patient_x
   ├─.dcm
   ⋮
   └─.dcm


**Naming Format:**

When sorting, the information obtained from the header of the dicom file determines the {folder name} & {subfolder name}.

folder: {PatientName}_{PatientID}
subfolder: {SeriesDescription}_{SeriesNumber}


**File directory tree of Classified dicom files:**

Classified_folder
├─{PatientName_1}_{PatientID_1}
│  ├─{SeriesDescription_1}_{SeriesNumber_1}
│  │  ├─.dcm
│  │  ⋮
│  │  └─.dcm
│  ├─{SeriesDescription_2}_{SeriesNumber_2}
│  │  ├─.dcm
│  │  ⋮
│  │  └─.dcm
│  ⋮
│  └─{SeriesDescription_i}_{SeriesNumber_i}
│     ├─.dcm
│     ⋮
│     └─.dcm
├─{PatientName_1}_{PatientID_1}
⋮                ⋮


### Multi Processing

At first, I just wrote the code and ran it(without multprocessing), but it was too slow.
So I used multiprocessing.

The following is the process using multiprocessing.

1. set the number of processes.

2. Assign tasks to each process according to the number of processes.

3. Run each process.

```python
process_l = list()
for i, dir in enumerate(dir_list):    # Define a process, add to the list
      p = Process(target=create_dcm_folder, args=(i, new_path, dir))    # create_dcm_folder: function to be executed by each process
      p.start()
      process_l.append(p)
for p in process_l:
      p.join()
```


[GitHub Link](https://github.com/somersaultFrog/dicom-file-classifier)


* Did you know? Frogs **cannot** live in the sea.