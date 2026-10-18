# Cross-working condition migration diagnosis new scheme! MS-DACAN multi-scale domain adaptive conditional alignment bearing fault diagnosis network

Preface\tIntelligent fault diagnosis for rolling bearings under fixed conditions can achieve high recognition accuracy. However, the load, speed, equipment, sensor position, and noise environment in the engineering site continuously change, leading to a significant domain shift between training data (source domain) and practical application data (target domain).\tTo address this issue, we propose an innovative transfer learning solution for rotating machinery, especially for fault diagnosis tasks involving rolling bearings: \tMS-DACAN\t (Multi-Scale Domain-Adaptive Class-conditional Alignment Network).\tMS-DACAN addresses the cross-fault diagnosis problem of "training and actual deployment scenarios differ" for rolling bearings by obtaining stable fault representations with an \tAdaptive Multi-Scale\t 1D CNN,\t eliminating the overall operational differences between the source and target domains with \tDANN,\t and further precisely aligning the same type of faults across two operating conditions with \tHigh Confidence Pseudo Labels Driven\t Class-conditional MK-MMD,\t and stabilizing the transfer process through \tProgressive Domain Adaptation + Entropy Minimization\t of the target domain. This achieves a unified cross-domain diagnosis that preserves fault information, weakens operational information, aligns similar features, and clarifies the boundaries of the target.
● Dataset: CWRU West Reserve University Bearing Dataset
1. Model Introduction
1.1 Overall Architecture of the Model
MS-DACAN is a framework for unsupervised transfer learning in the cross-conditional fault diagnosis of rotating machinery. The model addresses the practical scenario where "training conditions have labels, deployment conditions do not, and the data distribution changes." It perceives local impacts, periodic patterns, and long-scale modulation information through three-level adaptive multi-scale convolutions, and employs scale attention to select the most suitable receptive fields for different fault dynamics. In the transfer phase, DANN first reduces the operational differences between the source and target domains from a global perspective, followed by a class conditioned MK-MMD that fine-tunes cross-domain matching for the same fault category with high confidence pseudo-labels, and stabilizes the target decision boundary through minimizing target domain entropy and an iterative domain adaptation strategy. Its core is not merely to pursue "the two domains being more similar," but to achieve "closer within the same category, still separate for different categories, reduced operational identity, clearer target predictions," thereby enhancing the model's generalization diagnostic capability under unknown or changing operational conditions.
\t  
1.2 Introduction to Model Innovation Points
Innovation Point 2: DANN Global Domain Adversarial Attack - Eliminate "Working Conditions Identities" It does not independently undertake all migration tasks, but rather provides a more stable shared space for subsequent category-condition alignment. 3. Innovation Point: Upgrade from "Overall Alignment" to "Similarity Precision Alignment" of a Double-Layer Domain Adaptation CC-MK-MMD further refines the proximity of the same fault category within two domains. In cross-condition fault diagnosis, there is a natural conflict between "domain invariance" and "classification discriminability." Only emphasize the domain alignment can easily over-mix, only emphasize source domain classification cannot solve the situation change. Double-level alignment is maintained by the \t domain-level\t + category-level\t two constraints.
Innovation Point 4: Gradual Domain Adaptation Intensity Scheduling - Ensuring Migration Progresses from Weak to Strong with Stable Intervention
During the initial stages of training, features are approximately random. If at this point DANN and MK-MMD immediately impose maximum weight constraints on the network, the model is forced to align without yet forming a category structure, which can lead to collapse of class boundaries.
2 Experimental Design
2.1 Import Data
Refer to the previous article, conducting preprocessing for the \u0026\u0026\u002B University of Kansas bearing data set:
2.2 Specific handling
(1) Data partitioning principle: Original continuous records are first divided into regions, and then windows are cut within each region.
3. Fault Diagnosis Model Based on MS-DACAN
3.1 Definition of the Network Model
3.2 Setting Up Parameters and Training the Model
3.3 Model Evaluation: Using the 1HP->2HP Transfer Task as an Example
    (1) Accuracy, Precision, Recall, F1 Score
    (2) Confusion Matrix for Target Domain Fault Classification
    (3) t-SNE Feature Visualization After Model Training:
3.4 Explanability Analysis
    (1) Multi-Scale Attention Visualization
    The learning of attention weights reveals a clear hierarchical evolution of receptive field preferences. In the first stage, contributions from all four convolutional scales are relatively balanced, while in the second stage, emphasis is gradually placed on medium to large receptive fields. By the deepest stage, the network exhibits bimodal preferences for both the smallest and largest kernels, with k=31 and k=3 achieving the highest average weight. This indicates that advanced fault discrimination benefits from local transient structures and complementary integration of broader temporal contexts.
    (2) Category Scale Attention Visualization
Scale Attention Graphs for specific categories demonstrate clear dependence on scale selection. For example, Ball-0.007 strongly supports a k=31 branch, while Ball-0.014 exhibits a dominance preference for k=3. Similarly, for severe outer ring failures, similar shifts are observed. These results suggest that the optimal time receptive field is not fixed based on the fault category or severity, thereby supporting the necessity of adaptive multi-scale representation learning.
\t3.5 Partial Task Experimental Analysis
\t  
\tIn all the cross-load transfer tasks, MS-DACAN consistently outperforms pure source models. The average diagnostic accuracy improved from 95.73% to 98.65%, and the average F1 score increased from 94.11% to 98.20%. Observations of the maximum improvement in the 0HP→3HP transfer task showed an accuracy increase of 5.04 percentage points and a F1 score increase of 7.42 percentage points, demonstrating the effectiveness of domain adaptation under significant operational condition changes.
Click to download: Complete original data, Python code
END  
2. Friends who enjoy the content can follow, give the article a "like", share on social media or discuss in groups.
Previously Featured Content:
Rapid Document | Parallel Fault Diagnosis Model Based on 2D-SWinTransformer+1D-CNN-SENet
Significant update on bearing life prediction! New ensemble of CNN-BiGRU-Attention models + enriched visualization charts
Multimodal - Fault Diagnosis | The Big Core Convolution Opens a New Era in Vision!
Superior! Directly write in Zone One! Based on SSA+Informer-SENet Fault Diagnosis Model
Multi-source Information Fusion: Fault Diagnosis Model with Data Layer and Feature Layer Fusion!

## Images

<!-- PAYMENT_BLOCK -->

## Get this dataset

- Payment link (Stripe): [Buy now](https://buy.stripe.com/3cs8yP7sY87d0vu9AB)
- Payment QR code: ![Payment QR code](pay.png)

<!-- /PAYMENT_BLOCK -->
