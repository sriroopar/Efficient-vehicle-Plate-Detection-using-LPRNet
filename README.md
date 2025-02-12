# Efficient_Vehicle_Plate_Detection_LPRNet

Final Project for CSC591 - Real Time AI course. Model and MLC optimizations on existent LPRNet Vehicle Plate Detection Network.

# Description
LPRNet Model is widely used to perform vehicle plate detection. Our goal is to improve the efficacy of the model by incorporating certain model and MLC optimizations for real-time use cases.

# Instructions to Run the Notebook

1. Download the .ipynb file and Upload it to Google Colab (OR) [Use this link to Google Colab.](https://www.codecademy.com/pages/contribute-docs) to execute the notebook.
2. Connect to the GPU resource (T4 GPU) and run all the cells.
3. ONXX files and result csv files can be found in the filer explorer section.
4. Speed, Accuracy and Size are printed out as tables at individual levels of the project which will be indicated by the documentations above them.

# Optimizations

## Model Optimizations

Inorder to reduce the running time and space, we experimented with Fusion, Pruning and Quantization. Fusion offered a great level of compression with an accuracy trade-off. Pruning on the other hand was very effective in compressing the model by eliminating half of the weights. Quantization was helpful in reducing inference time and computationally decreasing the number of FLOPS required.

## MLC Optimizations

MLC Optmizations optimizes the LPRNet vehicle plate recognition model using TVM, applying custom relay optimization passes like operator fusion, loop vectorization, and inference simplification to reduce model size and improve inference speed. It also includes an auto-tuning pipeline using TVM’s autotvm, tuning key model layers with XGBTuner for enhanced performance. Both custom and auto-tuned models are evaluated against the original model based on accuracy and inference time, ensuring efficient deployment on edge devices.


# Results across metrics

We tried two different combinations of incorporating model optimizations and MLC optimizations by using the fused model for MLC using autotuning and pruned model for MLC using autotuning. The below table indicates the metrics for our best choice model which is and the original model. The inference time is obtained here on CPU. Our final decison was to go with the fused-autotuned model. 

| Metrics / Model         | Original LPRNet Model | Optimized LPRNet Model |
|------------------------|-------------------------|-------------------------|
| **Test Accuracy**       |          90.10            |         89.4               |                        
| **Inference Time**      |          159.4 ms               |        152.25 ms                |
| **Model Size**       |           1.71              |            1.704             |

