# Detection for Chat-GPT Teks

## Description 
Penelitian ini membahas implementasi model pre-trained BERT untuk mendeteksi teks buatan ChatGPT. Tujuan utama dari penelitian ini adalah:
1. Mengetahui pengaruh panjang data terhadap akurasi model.
2. Mengevaluasi performa model BERT dengan dua optimizer yang berbeda, yaitu **SGD** dan **AdamW**.

## Dataset 
Data yang digunakan adalah gabungan dari data [“ChatGPT Classification Dataset”](https://www.kaggle.com/datasets/mahdimaktabdar/chatgpt-classification-dataset) dan [“GPT vs. Human: A Corpus of Research Abstracts”](https://www.kaggle.com/datasets/heleneeriksen/gpt-vs-human-a-corpus-of-research-abstracts).   
Dataset yang digunakan memiliki dua macam (masing-masing berjumlah 456), yaitu 
1. Dataset kurang dari 200 kata : Jumlah kata paling sedikit adalah 26 dan yang terbanyak adalah 199. 
2. Dataset lebih dari 200 kata : Jumlah kata paling sedikit adalah 201 dan yang terbanyak adalah 456.
     
Dalam pengumpulan dataset ini, terdapat beberapa tahap. Tahap pertama, kedua dataset awal akan dibagi menjadi dua kategori, yaitu dataset dengan kata kurang dari 200 dan dataset dengan kata lebih dari 200. Selanjutnya, kategori dari kedua dataset akan digabungkan. Setelah itu, dilakukan analisis terhadap persebaran kelas pada masing-masing kategori. Agar masing-masing kategori memliki jumlah yang sama, dilakukan pemotongan data berdasarkan jumlah kelas terendah. 

## Alur Penelitian
1. **Pengumpulan Data**
   - Dataset diperoleh dari Kaggle.
2. **Preprocessing**
   - **Data Cleaning**: Menghapus elemen tidak relevan seperti tanda baca.
   - **Case Folding**: Mengubah seluruh teks menjadi huruf kecil.
3. **Pembagian Dataset**
   - Data dibagi dengan rasio: 
     - 75% Training
     - 15% Testing
     - 10% Validation
4. **Tokenization**
   - Menggunakan tokenizer BERT-base.
5. **Model Training**
   - Optimizer yang digunakan:
     - **SGD** (dengan momentum).
     - **AdamW** (dengan weight decay).
   - Parameter:
     - Learning Rate: 0.00003
     - Dropout: 0.2
     - Batch Size: 32
     - Epoch: 5
6. **Evaluasi Model**
   - Menggunakan Confusion Matrix.
  
## Hasil Penelitian
### Skenario 1: Optimizer SGD
- **Dataset Kurang dari 200 Kata**
  - Akurasi: 96%
  - Loss: 0.17
    
- **Dataset Lebih dari 200 Kata**
  - Akurasi: 97%
  - Loss: 0.073

### Skenario 2: Optimizer AdamW
- **Dataset Kurang dari 200 Kata**
  - Akurasi: 97%
  - Loss: 0.086
- **Dataset Lebih dari 200 Kata**
  - Akurasi: 97%
  - Loss: 0.18
