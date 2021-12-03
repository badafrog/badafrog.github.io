---
layout: post
title: Dicom Classifier
subtitle: File classification using python & multiprocessing
categories: python
tags: [python, work]
---

### What is a DICOM file?

A DICOM file is an image saved in the **Digital Imaging and Communications in Medicine**(DICOM) format.<br/>
It contains an image from a medical scan, such as an ultrasound or MRI.<br/>
DICOM files may also include identification data for patients to link the image to a specific individual.<br/>
\- [Reference:fileinfo.com](https://fileinfo.com/extension/dicom#:~:text=A%20DICOM%20file%20is%20an,as%20an%20ultrasound%20or%20MRI.&text=It%20was%20designed%20to%20exchange,%2C%20MRIs%2C%20and%20ultrasound%20images.)

### Classification

**File directory tree of Unclassified dicom files:**


~~~
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
~~~




**Naming Format:**

When sorting, the information obtained from the header of the dicom file determines<br/>
{folder name} & {subfolder name}.

Folder: {PatientName}\_{PatientID}<br/>
Subfolder: {SeriesDescription}\_{SeriesNumber}




**File directory tree of Classified dicom files:**

~~~
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
~~~


### Multi Processing

At first, I just wrote the code and ran it(without multiprocessing)<br/>
It was too slow. So I used multiprocessing.

The following is the process using multiprocessing:

1. Set the number of processes.

2. Assign tasks to each process according to the number of processes.

3. Run each process.

{% highlight python linenos %}
process_l = list()
for i, dir in enumerate(dir_list):    # Define a process, add to the list
      p = Process(target=create_dcm_folder, args=(i, new_path, dir))    # create_dcm_folder: function to be executed by each process
      p.start()
      process_l.append(p)
for p in process_l:
      p.join()
{% endhighlight %}


**GitHub Link**: <https://github.com/badafrog/dicom-file-classifier>
 <br/>
 <br/>
 <br/>

* Did you know? Frogs **cannot** live in the sea.