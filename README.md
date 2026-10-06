<div align="center">

# Noise Filter Lab: Image Denoising and Object Analysis

![Release Date](https://img.shields.io/github/created-at/D4rk-Pho3nix/sem7-cv-task1?style=flat-square&label=released&color=green)
![Last Commit](https://img.shields.io/github/last-commit/D4rk-Pho3nix/sem7-cv-task1?style=flat-square&label=last%20commit&color=purple)
[![Followers](https://img.shields.io/github/followers/D4rk-Pho3nix?style=flat-square&logo=github&color=yellow)](https://github.com/D4rk-Pho3nix)
[![Contact](https://img.shields.io/badge/Contact-Dev-cyan?style=flat-square)](mailto:manish.srmist23@gmail.com)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/D4rk-Pho3nix/sem7-cv-task1/blob/main/image_filter_experiment.ipynb)

A single Jupyter notebook that adds noise to images, removes it with four classic filters (mean, Gaussian, median, bilateral), then counts and measures the objects in each result to see how the filter choice changes them.

**made with 🩷 by [D4rk-Pho3nix](https://github.com/D4rk-Pho3nix)**

*(if you like my work, consider ⭐ starring the repo!)*

</div>

## Table of Contents

- [💡 Why this exists](#-why-this-exists)
- [✨ Features](#-features)
- [🏗️ Architecture](#-architecture)
- [🚀 Quick Start](#-quick-start)
- [📖 Usage](#-usage)
- [🎗️ Maintainers](#-maintainers)
- [🩷 Contributors](#-contributors)
- [💖 Support](#-support)
- [📄 License](#-license)

## 💡 Why this exists

Choosing a denoising filter by picture quality alone can be misleading. A filter can score well on PSNR and still blur edges or merge objects, which breaks later steps like counting.

This notebook runs the whole experiment for you. It applies each filter to each noise type, scores the results, and checks whether the "best looking" filter is also the best one for object analysis. Every number is computed when you run it.

## ✨ Features

- Needs no input files. It tries to download a sample image, falls back to one bundled with scikit-image, and always generates two synthetic images of its own.
- Four noise types: Gaussian, salt-and-pepper, speckle and Poisson.
- Four filters: mean, Gaussian, median and bilateral.
- Scores every result with MSE, RMSE, PSNR, SSIM, an edge-preservation score and runtime.
- Picks the best filter per noise type from a combined score, not PSNR alone.
- Segments and counts objects (Otsu threshold, morphology, watershed) on clean, noisy and filtered images.
- Measures shape descriptors: area, perimeter, centroid, bounding box, aspect ratio, circularity, eccentricity and solidity.
- Saves comparison grids, edge maps, segmentation overlays, plots, a CSV and a written summary.
- Fixed random seed (42), so runs are reproducible.

**Limitations**

- The "true count" is what the segmentation finds on the clean image. It is not a hand-labelled count.
- Filter settings are fixed (for example a 5x5 kernel). They are not tuned per image.
- Segmentation uses basic classical methods, so it can miscount crowded or low-contrast scenes.
- Runtimes depend on your hardware.

## 🏗️ Architecture

```text
sem7-cv-task1/
├── image_filter_experiment.ipynb   # the whole experiment
├── understanding.md                # beginner-friendly walkthrough of the code
├── README.md
└── output_imgs/                    # created when you run the notebook
    ├── original/                   # input images
    ├── noisy/                      # images with noise added
    ├── filtered/                   # denoised images
    ├── segmentation/               # object outlines and counts
    ├── comparisons/                # side-by-side grids and edge maps
    ├── plots/                      # bar charts
    ├── results.csv                 # all numbers
    └── final_summary.txt           # written conclusions
```

How the notebook works:

1. Get or generate the input images.
2. Add each noise type.
3. Apply the four filters and time them.
4. Score quality, edges, object counts and shape descriptors against the clean image.
5. Save images, plots and `results.csv`.
6. Print the best filter per noise type and a final analysis.

## 🚀 Quick Start

```bash
git clone https://github.com/D4rk-Pho3nix/sem7-cv-task1.git
cd sem7-cv-task1
```

**Google Colab (recommended)**

1. Open [`image_filter_experiment.ipynb`](image_filter_experiment.ipynb) in Colab using the badge above, or upload the file.
2. Choose Runtime > Run all.
3. The last cell offers `output_imgs.zip` for download.

**Locally** (Python 3.9 or newer)

```bash
python -m venv .venv
.venv\Scripts\activate          # Windows
# source .venv/bin/activate     # macOS / Linux
pip install numpy opencv-python scikit-image pandas matplotlib requests jupyter
jupyter lab
```

Then open `image_filter_experiment.ipynb` and run all cells. No GPU is needed.

## 📖 Usage

Run the cells in order. The first code cell installs the dependencies, and the last one shows a few results and zips the output folder.

To use your own images, add them to the dictionary returned by `download_or_generate_images()`, for example `images["mine"] = cv2.imread("photo.jpg")`. Pick photos with several distinct objects on a plain background so counting is meaningful.

Output in the notebook:

```text
BEST OVERALL FILTER PER NOISE TYPE
Noise Type       Best Overall Filter
------------------------------------
Gaussian         ...
...
```

Your own run fills in the table, the counting summary and the final analysis. The same text is saved to `output_imgs/final_summary.txt`.

## 🎗️ Maintainers

- [D4rk-Pho3nix](https://github.com/D4rk-Pho3nix)

## 🩷 Contributors

- [D4rk-Pho3nix](https://github.com/D4rk-Pho3nix)

## 💖 Support

If this saved you some time, you can support the work here:

[![Buy Me A Coffee](https://img.shields.io/badge/Buy%20Me%20A%20Coffee-support-yellow?style=flat-square&logo=buymeacoffee)](https://buymeacoffee.com/d4rkpho3nix)

## 📄 License

No license file has been added to this repository yet. The notebook depends on NumPy, OpenCV, scikit-image, pandas, Matplotlib and Requests, which are each licensed by their authors.

<div align="center">

[⬆ Back to Top](#noise-filter-lab-image-denoising-and-object-analysis)

<br>

[![Star History Chart](https://api.star-history.com/svg?repos=D4rk-Pho3nix/sem7-cv-task1&type=Date)](https://star-history.com/#D4rk-Pho3nix/sem7-cv-task1&Date)

</div>
