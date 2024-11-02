# ComputerVision
CV team project (A+)

### Problem Description
<img width="422" alt="image" src="https://github.com/iey704/ComputerVision/assets/105503671/67623a8b-078f-4d94-9e43-052df9c2197a">

- [ ] Improve "fine-grained classification" accuracy by modifying the model
- [ ] "Fine-grained dataset": refers to a dataset where the categories or classes are finely divided or detailed (object recognition, image classification, segementation, attribute recognition)

### 기존 코드
- [ ] Best Accuracy: 92.9054%
- [ ] Test Loss: 0.3288, Accuracy: 90.2685%
- [ ] Elasped Time: 22m 30s
<img width="458" alt="image" src="https://github.com/user-attachments/assets/d45e7eae-a78f-4e6a-9af4-0998a8136cd1">

### Experiments
**1. Augmentation - Geometric Transformation + Visual Corruptions)**
<p/>
<img width="458" alt="스크린샷 2024-11-02 오후 1 32 26" src="https://github.com/user-attachments/assets/215b7a59-5345-44f7-8224-07073eab67a6">
<p/>
* Geometric Transformation: Movement, Size, Rotation, Symmetry Transformation
* -> Apply vertical and horizontal flip (left and right inversion, upper and lower inversion), rotate 
* Visual Corruptions: 
- Images are exposed to various environmental noises, and images with noise affect model performance.
- We want to increase the robustness of our model by using visual corruption, which is a disturbance such as noise and blur.
-> gaussian noise, contrast, brightness

**2. Optimizer - AdamP:**
- an optimizer that inhibits excessive weight norm growth by eliminating gradient components parallel to the weight direction caused by momentum through projection.
  
**3. Hyperparameter(BATCH_SIZE, EPOCH, lr):**
<p/>
<img width="458" alt="스크린샷 2024-11-02 오후 1 39 00" src="https://github.com/user-attachments/assets/6e44c850-8470-4ce7-afd3-cf9cafcf095c">
<p/>
- The smaller the batch size, the better the performance
- The more you learn by repeating the epoxy, the better the performance
- The lower the learning rate, the better the performance

**4. Scheduler: get_cosine_schedule_with_warmup**
<p/>
<img width="458" alt="스크린샷 2024-11-02 오후 1 39 08" src="https://github.com/user-attachments/assets/f9ea311a-7232-437a-8af1-0221e23a0401">
<p/>
- After a warm-up period that increases linearly by the specified value (three times the train_loader) 
- In the optimizer, the schedule is generated with a learning rate that decreases with cosine function values.
-> This allows you to get out of saddle point quickly.
-> Congestion segments that occur in the middle of learning can also be quickly removed
-> Maximize model generalization performance
  
**5.Label Smoothing**
  <p/>
<img width="458" alt="image" src="https://github.com/user-attachments/assets/49905389-23a0-40b1-a79a-882336621e1e">
  <p/>
- A method to reduce overconfidence in deep learning predictions by softening Hard label (which consists of 1 correct answer index with one-hot encoded vector and 0 for the rest).

### Model
**Efficientnet b0 model**
<p/>
<img width="458" alt="스크린샷 2024-11-02 오후 1 45 30" src="https://github.com/user-attachments/assets/b8d58c02-28a7-488c-8e95-fdbcea4ec7e4">
<p/>
- There are three ways to improve performance: "Compound Scaling",
(1) Increase the depth of the network (increase the number of layers)
(2) Increase channel width (increase the number of filters)
(3) Increase the resolution of the input image 
- EfficientNet is a model that can find the best combination for three methods, using all three scaling, performing well with less FLOPS (calculated amount) than conventional models.

### Final Result
[FINAL] 
- [ ] Test Loss: 0.3447,Accuracy: 94.6309%
- [ ] Best Accuracy:  94.5945945945946
- [ ] Elapsed Time: 2h, 12m, 26s
- [ ] time: 2h, 12m, 26s

<img width="458" alt="스크린샷 2024-11-02 오후 1 47 29" src="https://github.com/user-attachments/assets/cebf9a7f-0f82-4eff-a645-8aab7efdaea3">
<img width="458" alt="스크린샷 2024-11-02 오후 1 47 48" src="https://github.com/user-attachments/assets/85d7c616-94e3-48f6-8d12-c61fa5bf4363">
<img width="458" alt="스크린샷 2024-11-02 오후 1 47 55" src="https://github.com/user-attachments/assets/d6e6e90f-8d24-406e-b0e7-77a3257b01f7">
<img width="458" alt="스크린샷 2024-11-02 오후 1 47 58" src="https://github.com/user-attachments/assets/05bb8460-7244-4b50-be23-01ffbab71a9f">
<img width="458" alt="스크린샷 2024-11-02 오후 1 48 00" src="https://github.com/user-attachments/assets/0457162a-5fe8-4127-9a3f-f928d65f3ae8">
