---
name: Multimodal Integration
tools: [scanpy,anndata, maxfuse]
# image: https://www.sketchappsources.com/resources/source-image/movie-badges-jurajjurik.png
description: Improve the integration of single-cell multi-omics data
---

# Multimodal Integration
<p class="text-center">
{% include elements/button.html link="https://github.com/DebDDash/ComputationalGenomics/tree/main/Final_Project_Multimodal_Integration" text="Github" style="primary" size="sm" %}
</p>

The integration of diverse single-cell datasets poses significant challenges, particularly as datasets increase in size and complexity. Current methods typically depend on shared features between datasets, which restricts their scalability and effectiveness. Utilizing deep generative models, such as VAEbased or GAN-based architectures, offers a unified solution to overcome these limitations, enhancing the integration process and supporting more in-depth analyses. Mosaic integration refers to the computational process of aligning and combining datasets that capture distinct molecular modalities from singlecell or spatial omics studies.

# Dataset Information
All datasets are publicly available. For convenience, we have included code to download the datasets at the beginning of each notebook which will download the dataset for you. The details of the datasets used are -

1. CiteSeq PBMC - The CITE-seq healthy human PBMC dataset with 228 antibody markers was obtained from [Hao et al](https://arxiv.org/abs/1610.03454). for benchmarking.
2. TeaSeq - The TEA-seq neutrophil-depleted human PBMC dataset (GSM4949911) was obtained from [from Swanson et al](https://pubmed.ncbi.nlm.nih.gov/33835024/)

# Method Overview
scMODAL is a deep generative model that integrates single-cell multi-omics data by learning shared latent representations across modalities. It starts by identifying biologically linked features (e.g., gene expression with gene activity or protein levels) and inputs full cell-by-feature matrices into nonlinear encoders, preserving biological variation. These encoders project cells into a shared latent space, while decoders reconstruct the input to maintain consistency. To align latent distributions, scMODAL uses a GAN-inspired discriminator and Jensen-Shannon divergence. To avoid mismatches between distinct cell types, it introduces mutual nearest neighbors (MNNs) across modalities as soft anchors, applying an L2 penalty on their embedding distances. Additionally, it preserves local geometry using Gaussian kernel distances. The trained model enables aligned cell representations, cross-modality mapping, and feature imputation to uncover regulatory interactions.
<p align = "center">
    <img src="/assets/method.png" width= "60%"/>
</p>

# Results
scMODAL integration: of the PBMC dataset resulted in a label transfer accuracy of 97.96% and a FOSCTTM score of 0.00092.
<p align = "center">
    <img src="/assets/scmodalres.png" width= "60%"/>
</p>
