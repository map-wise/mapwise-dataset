# MAPWise: Evaluating Vision-Language Models for Advanced Map Queries

## Overview
This dataset contains map visualizations spanning three countries (USA, China, and India), along with counterfactual variants. It is designed to understand and improve the effectiveness of Vision-Language Models on map interpretation tasks.

## Dataset Structure
```
├── china/
│   ├── images/ (this contains the images for the maps)
│   │   ├── hatched/ 
│   │   ├── with_annotations/
│   │   └── wo_annotations/
│   ├── json_data/ (this contains the questions presented in json format)
│   │   ├── hatched.json
│   │   ├── with_annotations.json
│   │   └── wo_annotations.json
│   ├── metadata/ (this contains the metadata for the maps)
│   │   └── [multiple map JSON files]
│   └── qna.csv (this contains the questions and answers for the maps, presented in csv format)
├── counter_factuals/
│   ├── imaginary/
│   ├── jumbled/
│   ├── original/
│   └── shuffled/
├── india/
│   ├── images/
│   ├── json_data/
│   ├── metadata/
│   └── qna.csv
├── usa/
│   ├── images/
│   ├── json_data/
│   ├── metadata/
│   └── qna.csv
├── README.md
└── template.csv
```

## Data Description

### Map Metadata
Each map's metadata JSON file contains:
- **map_id**: Unique identifier for each map
- **map_type**: Visualization type (predominantly Choropleth)
- **scope**: Geographic coverage (USA, China, India)
- **locationmode**: Location identification system (e.g., "USA-states")
- **projection**: Map projection used (e.g., "albers usa")
- **legend_type**: Either "Discrete" or "Continuous"
- **legend_order**: Direction of legend values
- **data_type**: Type of data represented (e.g., "Number", "Percentage")
- **data**: Array of region-specific values

This metadata file is useful for the process of re-creating the exact dataset using plotly or other visualization libraries.

---

### Visualization Variants
For each country, multiple visualization styles are available:
- **Hatched**: Maps using pattern fills instead of solid colors
- **With annotations**: Maps containing additional textual or graphical annotations to represent the names of the regions 
- **Without annotations**: Basic choropleth maps

---

### Counterfactual Maps
The `counter_factuals/` directory contains alternative map versions:
- **Original**: Unmodified reference maps
- **Shuffled**: Maps with shuffled region-value assignments
- **Jumbled**: Randomized or mixed data
- **Imaginary**: Fictional or hypothetical data representations

---

### Question-Answer Data
Each country's directory includes a `qna.csv` file containing questions and answers related to the maps, designed for evaluating comprehension of different visualization formats.

Each question answer file contains the questions - `question`, the maps associated with those questions - `map_id` and the ground truth answers - `ground_truth`. In addition to that, each row also containts metadata about if the map has a continuous or discrete legend - `c_or_d` and if the given question has reference to regions relative to a given region - `relative_region`.

Each question can be evaluated on maps with or without annotations. However, only questions which have the continuous or discrete legend type marked as `d` can be evaluated on hatched maps.

## Research Applications

This dataset is particularly valuable for research on understanding and evaluating Vision Language Models and Multimodal Langauge Models on map interpretation tasks. This dataset was used to evaluate multimodal models and to understand the limitations of current multimodal models for this task.

We hope this dataset can also be used in building more interpretable and robust multimodal models for understanding maps.

## Citation

When using this dataset, please cite:
```bibtex
@misc{mukhopadhyay2024mapwiseevaluatingvisionlanguagemodels,
      title={MAPWise: Evaluating Vision-Language Models for Advanced Map Queries}, 
      author={Srija Mukhopadhyay and Abhishek Rajgaria and Prerana Khatiwada and Vivek Gupta and Dan Roth},
      year={2024},
      eprint={2409.00255},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2409.00255}, 
}
```