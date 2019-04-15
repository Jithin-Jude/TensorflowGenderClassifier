# TensorflowGenderClassifier
Classify gender based on face image.

Train model
-
```
py -3 -m scripts.retrain   --bottleneck_dir=tf_files/bottlenecks   --model_dir=tf_files/models/"${ARCHITECTURE}"   --summaries_dir=tf_files/training_summaries/"${ARCHITECTURE}"   --output_graph=tf_files/retrained_graph.pb   --output_labels=tf_files/retrained_labels.txt   --image_dir=tf_files/gender
```

Run model
-
```
py -3 -m scripts.label_image     --image=tf_files/gender/female/20_1_0_20170109213411083.jpg.chip.jpg
```

References
-
https://medium.com/datadriveninvestor/building-an-image-classifier-using-tensorflow-3ac9ccc92e7c

https://github.com/googlecodelabs/tensorflow-for-poets-2
