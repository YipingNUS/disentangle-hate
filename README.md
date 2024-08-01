# Accompanying code for ARR August 2024 Manuscript

Accompanying code for the manuscript "Disentangling Hate Across Target Identities".

## Description of Repo

**Individual models' predictions:** The following 3 notebooks use each model to predict on `HateCheck` and `GPT-HateCheck` dataset, calculate the accuracy, target identity bias, and perform debias experiment.

- [HateBERT Evaluation.ipynb](<HateBERT Evaluation.ipynb>)
- [ToxDect-roberta Evaluation.ipynb](<ToxDect-roberta Evaluation.ipynb>)
- [Perspective API Evaluation.ipynb](<Perspective API Evaluation.ipynb>)

[RQ1 Minimum Set Bias.ipynb](<RQ1 Minimum Set Bias.ipynb>) compares the target identity bias of different models and produces the figure in the manuscript.

[Emotion Identification.ipynb](<Emotion Identification.ipynb>) extracts emotions from `GPT-HateCheck` and performs analysis.

[Stereotype Analysis.ipynb](<Stereotype Analysis.ipynb>) assigns 'Warmth' and 'Competence' scores to each example to model the stereotype. It also plots the correlation between the location in the semantic space and models' accuracy.

[Stereotype Identification.ipynb](<Stereotype Identification.ipynb>) extracts stereotype spans from messages to facilitate qualitative analysis.

## Running the code

### Environment

We conduct most of the experiments in CPU instances in Google Colab.

- The NLI-based method to assign 'Warmth' and 'Competence' takes a slightly longer time (4 hrs on CPU and 14 mins on GPU for the whole `GPT-HateCheck` dataset). 
- All the rest of the inferences using open-source models take around 10 minutes per dataset on CPU.
- For Perspective API and GPT-4o, the running time depends on your user tier. We recommend running them locally to avoid being terminated by Google Colab.

### Open-Source Models

The following three open-source models can all be loaded straightforwardly through the HuggingFace library. For usage instructions, please refer to the corresponding `README.md` and notebooks.

- `HateBERT_offenseval`
- `ToxDect-roberta-large`
- `nli-deberta-v3-large`



### Perspective API

Perspective API is free to use in the Google Cloud Platform. To set it up, please follow the [Get Started Guide](https://developers.perspectiveapi.com/s/docs-get-started?language=en_US).

We requested an increased QPS limit (10 QPS). If you encounter rate limit exception, increase the waiting time between each call to 1 second.

### GPT-4o

You need to create a paid OpenAI account to use GPT-4o. Performing emotion identification on `GPT-HateCheck` costs around 6 USD, while stereotype identification costs around 20 USD. The QPS varies greatly based on your user tier. It would take up to 2 day for the most basic tier and only 1-2 hrs for a higher tier.