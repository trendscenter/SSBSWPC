# SSB+SWPC: a novel method to estimate time resolved connectivity

This repo contains the implementation for the the method presented in  [Frequency modulation increases the specificity of time-resolved connectivity: A resting-state fMRI study
](https://www.biorxiv.org/content/biorxiv/early/2023/06/21/2023.06.20.545786.full.pdf) in both python and Matlab.

Codes "calculate_SSBSWPC.py" and "calculate_SSB_SWPC.m" are the main functions for the estimator in both languages, while "SSBSWPC_demo.ipynb" demonstrate the estimator use. We have tested this code on an Ubuntu Linux distribution with Python version 3.10.9.

If u use these codes please cite 

Faghiri, A., Yang, K., Ishizuka, K., Sawa, A., Adali, T., & Calhoun, V. (2023). Frequency modulation increases the specificity of time-resolved connectivity: A resting-state fMRI study. bioRxiv, 2023-06.


```python
@article{faghiri2023frequency,
  title={Frequency modulation increases the specificity of time-resolved connectivity: A resting-state fMRI study},
  author={Faghiri, Ashkan and Yang, Kun and Ishizuka, Koko and Sawa, Akira and Adali, Tulay and Calhoun, Vince},
  journal={bioRxiv},
  pages={2023--06},
  year={2023},
  publisher={Cold Spring Harbor Laboratory}
}
```

## A short summary of SSB+SWPC
Representing any set of time series using networks are used in many scientific fields. Historically, the constructed networks were constant throughout the whole temporal range of the data, but more recently time resolved networks have attracted a lot of attentions. One field where these time-resolved networks are used more and more is neuroimaging. Assuming we have the nodes of the human brain and their associated time series, the question is then finding the edges between these nodes in such a way that is time resolved. For functional data (e.g., functional magnetic resonance imaging or fMRI) the term time resolved functional connectivity (trFC) is often used to talk about these edges. Another related term to trFC is dynamic functional connectivity (dFC). Note that if the nodes are network themselves, we usually use the term time resolved functional network connectivity (trFNC) and dynamic functional connectivity (dFNC).
Many estimators have been suggested for estimating the trFC from a set of time series, but possible the most well-known one is sliding window Pearson correlation (SWPC). This method has been used extensively in many neuroimaging researches, but like any other method has some shortcomings. One major shortcomings of this method is that if we select very small window size, important low-frequency content of the time series might be filtered out. Therefore some papers suggest that we select a window size based on the __lowest__ frequency of the time series [1]. For example if our time series' spectrums are bounded between 0.01 and 0.1 Hz, they argue that we should chose a window size of __at least__ (approximately) 100 seconds. Although mathematically correct, this would mean that the __fastest__ connectivity being estimated have a frequency of 0.005 Hz, which is quite low. In recent works, we have proposed a method based on single side band modulation (SSB) that aim to remedy this issue [2, 3]. This method which after a flash of brilliance we call SSB+SWPC, allows us to select a window size without removing low-frequency information as those information are moved to higher frequencies in a fashion that does not impact the estimated correlation greatly.

### References

[1] Leonardi, N., & Van De Ville, D. (2015). On spurious and real fluctuations of dynamic functional connectivity during rest. Neuroimage, 104, 430-436.\
[2] Faghiri, A., Yang, K., Ishizuka, K., Sawa, A., Adali, T., & Calhoun, V. (2023). Frequency modulation increases the specificity of time-resolved connectivity: A resting-state fMRI study. bioRxiv, 2023-06.\
[3] Faghiri, A., Adali, T., & Calhoun, V. D. (2022, March). Single Sideband Modulation as a Tool To Improve Functional Connectivity Estimation. In 2022 IEEE 19th International Symposium on Biomedical Imaging (ISBI) (pp. 1-4). IEEE.