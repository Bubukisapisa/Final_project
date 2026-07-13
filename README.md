# Детекція об'єктів на аерознімках з БпЛА (VisDrone)

## Мотивація та аналіз ринку
Узагальнений список вимог до кандидата
🎯 Моделі та архітектури (ключовий аспект)
Must have — детекція та трекінг (ядро 90% вакансій):

YOLO-сімейство (v5/v8/v9/v11) — де-факто стандарт для real-time детекції на борту дрона; вакансії прямо називають YOLO/CNN базовою вимогою Djinni
CNN-архітектури загалом (ResNet, MobileNet/EfficientNet як backbone для edge)
Трекери: SORT / DeepSORT / ByteTrack (object tracking постійно йде в парі з detection)
Two-stage детектори для розуміння trade-offs: Faster R-CNN, Mask R-CNN (сегментація)
Задачі формулюються як object detection, classification, segmentation, tracking — повний цикл від тренування до деплою Djinni

Навігація без GPS (специфіка мілтеху — РЕБ глушить GPS):

SLAM / VIO: ORB-SLAM, OpenVINS — окремі вакансії шукають саме класичний CV: SLAM, Visual-Inertial Odometry, sensor fusion Dou
Image matching / image retrieval: keypoint detection & matching (класичні SIFT/ORB + нейромережеві SuperPoint/SuperGlue/LoFTR-клас) — детекція ключових точок і матчинг зображень фігурують як основні задачі, це основа візуальної навігації по супутникових знімках Djinni

Nice to have:

Reinforcement learning для автономного керування (окремі RL-вакансії з вимогою переносу з симулятора на борт, sim-to-real gap) Djinni
Генеративні моделі (аугментація даних, synthetic data)
Моделі для теплових/IR-зображень (EO/IR камери)

⚙️ Оптимізація та деплой на edge (друга за важливістю група)

TensorRT, ONNX — конвертація та прискорення інференсу (згадується майже в кожній вакансії)
Квантування (INT8/FP16) та прунінг моделей для стабільного FPS
Платформи: NVIDIA Jetson (Nano/Xavier/Orin), Raspberry Pi
Також OpenVINO, NVIDIA Triton для model serving Djinni

💻 Мови та інструменти

Python (основна) + C++ (для real-time/embedded — часто must have у senior-ролях)
PyTorch (домінує) або TensorFlow
OpenCV, NumPy
Linux (обов'язково), Docker, Git

🧮 Математика

Projective geometry, 3D-проекції, епіполярна геометрія
Лінійна алгебра, статистика, фільтри (Kalman/EKF для sensor fusion)
Алгоритми та структури даних

🚁 Доменні знання (сильний плюс)

ROS/ROS2 (nodes, topics, services), автопілоти ArduPilot/Betaflight/PX4, sensor fusion (камера + IMU + GPS), MAVLink Djinni
Симулятори: Gazebo, AirSim
Аеро/супутникові знімки, remote sensing, геопросторові дані
Розуміння real-time constraints (боротьба за мілісекунди інференсу на слабкому залізі)

Коротке резюме
Кандидат має вміти натренувати YOLO-подібний детектор на аеровідео, прикрутити до нього трекер, стиснути модель через TensorRT/квантування і запустити її на Jetson із стабільним FPS. Другий великий напрям — візуальна навігація в умовах відсутності GPS (SLAM/VIO + image matching по супутникових картах).
Класичний CV (OpenCV, геометрія) цінується не менше за deep learning — на борту дрона часто немає ресурсів для важких мереж.

## Задача
Multi-class object detection на аерознімках. Метрика: mAP@50.

## Дані
VisDrone2019-DET, N зображень, класи: ...

## Підхід
Baseline: zero-shot YOLOv8n (COCO). Моделі: ...

## Результати
| Модель | Параметри | val mAP50 | val mAP50-95 | Inference (ms) | Час тренування |
|-----------|----------:|----------:|
| Baseline: YOLOv8n (COCO, zero-shot)      | без тренування      | 0.016      | 0.007 | 3.1 | 0 |

## Висновки
[в кінці]

## Installation & Usage
[в кінці]