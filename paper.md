
### **Datasets for Image Captioning**
---
## **2. Flickr8k**

|**Details**|**Values**|
|---|---|
|**Images**|8,000|
|**Captions per Image**|5|
|**Total Captions**|40,000|

#### **Link:**

[Flickr8k Dataset Download (Kaggle)](https://www.kaggle.com/datasets/adityajn105/flickr8k)
---
## **3. Flickr30k**

|**Details**|**Values**|
|---|---|
|**Images**|31,783|
|**Captions per Image**|5|
|**Total Captions**|158,915|

#### **Link:**

[Flickr30k Dataset (Official Site)](http://shannon.cs.illinois.edu/DenotationGraph/)

---
## **4. Conceptual Captions (Google AI)**

|**Details**|**Values**|
|---|---|
|**Images**|~3.3 million|
|**Captions**|~3.3 million|
#### **Link:**
[Conceptual Captions Paper & Dataset](https://ai.google.com/research/ConceptualCaptions)
---
## **5. Visual Genome**

|**Details**|**Values**|
|---|---|
|**Images**|108,077|
|**Region Descriptions**|~5 million|
|**Objects & Attributes**|Detailed annotations|
#### **Link:**

[Visual Genome Dataset](https://visualgenome.org/)

---


---

### **Summary of Use Cases:**

|**Dataset**|**Use Case**|
|---|---|
|**Flickr8k/Flickr30k**|Academic learning, CPU setups|
|**MS COCO**|Benchmark, competitions|
|**Visual Genome**|Dense and region captions|
|**Conceptual Captions**|Pre-training large models|

---

## literature survey 
1. **Lin et al. (2025) – Panoptic Captioning**  
    Introduced a new task combining full-scene understanding and detailed description using the __PancapChain__ model. It emphasizes semantic richness, spatial coherence, and introduces a novel evaluation metric (_PancapScore_), outperforming major multimodal models.
    
2. **Hua et al. (2025) – FINECAPTION**  
    Proposed a compositional model that can generate image captions for any __arbitrary region__ within an image. The model is region-aware and instruction-guided, demonstrating strong generalization in localized captioning with their _OpenCompositionCap_ dataset.
    
3. **Graph-Based Captioning (2025)**  
    Used __Graph Convolutional Networks (GCNs) and relational transformers__ (RelTR) to capture spatial and semantic relationships between image objects. This method significantly enhances the model's ability to understand scene layout and object interactions.
    
4. **Fons et al. (2025) – TADACap**  
    Designed for __time-series chart images__, this retrieval-based model adapts across domains without retraining. It addresses a niche in the captioning domain—time-dependent visuals—ensuring context-specific and meaningful descriptions with minimal data annotation.
    
5. **Qu et al. (2024) – Context Modeling for Nmews Image Captioning**  
    Tackles image captioning in journalism by retrieving related article content using CLIP and generating context-aware captions. Their model showed a large performance gain on news image datasets like _GoodNews_ and _NYTimes800k_.
    
6. **Zhou et al. (2024) – CapFlow**  
    Combined captioning with hashtag generation for social media. Utilized __fine-tuned vision-language models__ with LoRA for efficiency and incorporated _KeyBERT_ for hashtag extraction, enabling both detailed and trendy visual content descriptions.
    
7. **Nguyen et al. (2022) – GRIT**  
    Developed a dual-feature __transformer-based model__ using both grid-level and region-level features extracted via DETR. The method achieves a good balance between performance and speed, offering improved results on benchmarks like _MSCOCO_.


## **List of recent pretrained models

|Model|Year|Type|Strength|Performance vs ConvNeXt|
|---|---|---|---|---|
|**ConvNeXt**|2022|ConvNet|Strong CNN baseline|—|
|**InternImage**|2023|ConvNet (DCNv3)|Best CNN, very high accuracy|🔥 Better|
|**CoaT v2**|2023|Hybrid (Conv + Attn)|Lightweight, efficient|🔁 Similar / better|
|**FocalNet**|2023|Modulated Conv|Efficient, transformer-like|🔁 Similar|
|**RepLKNet**|2022|Large-kernel CNN|Long-range context, high-res|🔁 Similar / better|
|**EfficientViT**|2024|Efficient ViT|Great speed/accuracy trade-off|✅ Better (small models)|
