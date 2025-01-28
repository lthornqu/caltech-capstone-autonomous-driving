# caltech-capstone-autonomous-driving
Capstone project from Caltech bootcamp. This capstone is broken into two problem statements and objectives, listed below. What follows is a detailed writeup of my process with an analysis of the results, challenges encountered, and potential ways to improve the model if I was consintently working on it.

Problem Statement 1: Autonomous vehicles (AV) and intelligent transport systems (ITS) are the future of road transport. Automatic detection of vehicles on the road in real-time helps AV technology and makes ITS more intelligent in terms of vehicle tracking, vehicle counting, and road incident response.

Objective Part 1: Develop an AI model using a deep learning framework that predicts the type of vehicle present in an image as well as localizes the vehicle by rectangular bounding box.

Problem Statement 2: Tesla, Inc. is an American multinational automotive and artificial intelligence company. In October 2020, Tesla started a full self-driving capability beta program in the United States. Tesla has over 100k people in this program.

Objective Part 2: As the second part of this project, you need to analyze the usage of autopilot and its effect on road safety.


Writeup:

For Part 1, I started by creating the parent and child folders along with the directory structures and paths for the images and labels data.

Later on I ended up manually changing around the directory structure because I originally did not set it up in the correct way for the YOLO model to properly train...so what you see in the source code is not quite accurate. I included an image in the repo showing the directory structure I ended up using (relevant folders highlighted by the green box).

Within my notebook I cleaned up the data, applied vehicle type mapping, standardized the labels, and saved the labels as YOLOv8 text files in the proper location.

I then split the images and labels into train, test, and val splits and moved them to the proper directories (again, I had to manually change their location at the same time as when I changed the directory structure).

We had significantly more data for the labels than images that matched, so I filtered out any labels that did not have a corresponding image.

The final step for preparing the dataset for training was to create my YAML file. I included a screenshot of what my file looks like in the repo.

Now I could move on to creating my CNN architecture. I originally started with a YOLOv5 model, and ran into a lot of errors. As I was looking around for solutions, I realized an updated model existed so I switched my model over to a YOLOv8. Since my file paths were already set and named, many of them still had YOLOv5 in their title but it didn’t matter for the actual training of the model.

I ran 5 epochs locally on my machine and it took 18 hours. I looked at ways to make this process faster and setting up virtual environments, but I decided to just keep this model for simplicity purposes. The results are attached in screenshots and in my source code, but below is a summary.

Overall Performance:

● Precision: 0.653

● Recall: 0.534

● mAP@0.5: 0.601

● mAP@0.5:0.95: 0.454

These values indicate moderate performance. Precision is higher than recall, suggesting that when the model predicts a vehicle, it is more likely to be correct, but it misses a fair number of actual vehicles (lower recall).
 
Class-wise Performance:

● pickup_truck: Precision (0.711) and recall (0.558) indicate decent performance but could be improved.

● car: This class has high precision (0.764) and recall (0.787), indicating strong performance.

● articulated_truck: Moderate performance with a precision of 0.554 and a recall of 0.667.

● bus: Excellent performance with high precision (0.924) and recall (0.879).

● motorized_vehicle and work_van: These classes show lower performance, indicating that the model struggles with these categories.

● single_unit_truck: Precision (0.585) is moderate, but recall (0.286) is low.

● pedestrian and bicycle: High performance with precision and recall close to 1, though the sample size is very small.

● non_motorized_vehicle: Perfect precision but zero recall, indicating a potential issue with detecting these objects.

● motorcycle: Moderate performance with a precision of 0.515 and recall of 0.25.

For future models, I would experiment with better fine tuning the model like data augmentation, different hyperparameters, and getting more images in my data.

Finally, I ran inferences on sample images to see how my model worked (some examples are included in the repo). It worked okay, but not as great as some the val results might have indicated.
