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
Convert .pb to .lite
-
```
IMAGE_SIZE=299
tflite_convert \
  --graph_def_file=tf_files/retrained_graph.pb \
  --output_file=tf_files/optimized_graph.lite \
  --input_format=TENSORFLOW_GRAPHDEF \
  --output_format=TFLITE \
  --input_shape=1,${IMAGE_SIZE},${IMAGE_SIZE},3 \
  --input_array=Mul \
  --output_array=final_result \
  --inference_type=FLOAT \
  --input_data_type=FLOAT
```

References
-
https://medium.com/datadriveninvestor/building-an-image-classifier-using-tensorflow-3ac9ccc92e7c

https://github.com/googlecodelabs/tensorflow-for-poets-2

https://codelabs.developers.google.com/codelabs/tensorflow-for-poets/#3

https://codelabs.developers.google.com/codelabs/tensorflow-for-poets-2-tflite/#2
