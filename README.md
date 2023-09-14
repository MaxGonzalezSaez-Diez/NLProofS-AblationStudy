# Generating Natural Language Proofs with Verifier-Guided Search: Diverse Beam Search, Aggregation Functions, and Verifier-Weighting in NLProofS

<p align="center">
  <img src="images/div_beam.png" alt="Task">
</p>
<p align="center"><a href="https://arxiv.org/abs/1610.02424">Vijayakumar et al., 2016</a></p>

We present the code and results for an ablation study of the paper [Generating Natural Language Proofs with Verifier-Guided Search](https://arxiv.org/abs/2205.12443) by [Kaiyu Yang](https://www.cs.princeton.edu/~kaiyuy/), [Jia Deng](https://www.cs.princeton.edu/~jiadeng/), and [Danqi Chen](https://www.cs.princeton.edu/~danqic/)  . 

## Abstract 

Hallucination of invalid nodes in stepwise proof generation poses a problem for natural language processing. Yang et al. (2022) address this issue with NLProofS, mitigating hallucination by using an auxiliary verifier model to guide the stepwise proof generation towards generating valid proof steps. In this study, we replicate the baselines of their work and expand their exploration in three primary directions: (1) varying the prover-verifier proof score weighting in scoring nodes in the proof tree, (2) incorporating diverse beam search for proof tree generation, and (3) evaluating alternative functions for aggregating the scores of nodes in the proof tree. Our highest-performing model achieved an overall proof accuracy of 36.28\% on the official Entailment Bank test dataset, therefore outperforming the (replicated) baseline score of 34.71\% achieved by the original NLProofS model.

## Quick Links

Any information regarding requirements, data preprocessing, experiments and datasets can be found [here](https://github.com/princeton-nlp/NLProofS).

## Ablation Results

#### Verifier Weighting Experiments

<table>
  <tr>
    <th>Verifier Weight</th>
    <th>Proof Accuracy (\%)</th>
  </tr>
  <tr>
    <td>0.8</td>
    <td>35.588 ± 0.588</td>
  </tr>
  <tr>
    <td>0.7</td>
    <td>35.784 ± 0.612</td>
  </tr>
  <tr>
    <td>0.5 (Baseline)</td>
    <td>34.706 ± 0.294</td>
  </tr>
  <tr>
    <td>0.3</td>
    <td>34.706 ± 0.294</td>
  </tr>
  <tr>
    <td>0.2</td>
    <td>34.804 ± 0.340</td>
  </tr>
</table>


#### Diverse Beam Search

| BG | DP | proof accuracy (in \%)               |   
|-------------------------------------------|---|---|
| 2  |	&minus; 10.0 | 35.882 ± 0.294                   |   
| 2 |	&minus; 5.0 | 36.275 ± 0.340                     |  
| 2 |	&minus; 2.0 | 36.176 ± 0.294                     |  
| 2 |	&minus; 0.8 | 35.784 ± 0.170                     |  
| 2 |	&minus; 0.5 | 36.078 ± 0.340                     |  
| 2 |	&minus; 0.2 | 36.078 ± 0.170                     |  
| 2 | 	0.8 | 33.824 ± 0.588                      |   
| baseline (1 BG, 0 penalty) | &minus; | 34.706 ± 0.294 |  

#### Aggregation Functions

| f <sub>&ast;</sub>| function | proof accuracy (in \%)   |  
|-------------------------------------|---|---|
| f<sub>1</sub> | baseline | 34.706 ± 0.294          |   
| f<sub>3</sub> | s<sup>2</sup>  min(v<sub>1</sub>, ..., v<sub>n</sub>) | 35.000 ± 0.588   |   
| f<sub>3</sub> | s<sup>3</sup> min(v<sub>1</sub>, ..., v<sub>n</sub>) | 35.196 ± 0.679   |   
| f<sub>3</sub> | s<sup>4</sup> min(v<sub>1</sub>, ..., v<sub>n</sub>) | 34.902 ± 0.170   |   
| f<sub>5</sub> | min<sub>1</sub>(I) · min<sub>2</sub>(I) | 35.098 ± 0.449 |   
| f<sub>8</sub> | min(v<sub>1</sub>, ..., v<sub>n</sub>)<sup>2&minus;s</sup> | 35.000 ± 0.588 |   

#### Conclusion

We replicate the findings by [Yang et al. (2022)](https://arxiv.org/abs/2205.12443) and then present a number of different
ablations to their baseline model. Our two main contributions are: first, setting the verifier score to 0.7 resulted in a proof accuracy of 35.78\%. Second our implementation of diverse beam search with 2 beam groups and a diversity penalty of &minus; 5.0 achieved a proof accuracy of 36.28\%. These results reveal an interesting direction for future work and demonstrate that additional studies are needed to better understand stepwise proof generation.

#### Acknowledgements
We extend our acknowledgments to Professor Danqi Chen for her guidance and advice on our project, as well as to Dr. Yang for his insightful comments on our paper.

## Bugs or Questions

If you have any questions related to the code or the paper, feel free to email [Max Gonzalez Saez-Diez](mailto:gonzalezsaezdiez@gmail.com). If you encounter any problems when using the code in this repository, please open an issue so we can update the codebase. Thank you!

