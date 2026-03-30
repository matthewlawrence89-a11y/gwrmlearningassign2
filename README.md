# gwrmlearningassign2
Generative AI was used to assist in creating and checking python code.

# Q2
Agreement:
SHAP and LIME tend to agree on the most influential features, particularly priors_count, age, and charge degree. In high-risk individuals, both methods assign strong positive contributions to prior offenses and more severe charges, while low-risk individuals show negative contributions from fewer priors and older age.

Divergence:
Differences arise because SHAP distributes contribution across all features using a global expectation baseline, while LIME fits a local surrogate model. As a result, LIME often produces sparser explanations and may overweight features that are locally influential but not globally important. Additionally, LIME explanations can vary across runs due to sampling instability, whereas SHAP is more consistent.

Governance implication:
Divergence indicates that explanations are method-dependent approximations, not ground truth . This creates risk in high-stakes settings: different explanation methods may justify the same decision differently. Therefore, governance frameworks should require multiple explanation methods, documentation of their assumptions, and consistency checks before using them in legal or policy contexts.

# Q4
The application of SHAP, LIME, and counterfactual explanations reveals consistent patterns in the model’s behavior. Across individuals, prior criminal history (priors_count), age, and charge severity emerge as the dominant drivers of predicted recidivism risk. SHAP’s global decomposition shows that prior offenses contribute the largest positive increases in risk, while age often reduces predicted risk. LIME explanations for the same individuals largely confirm these drivers, though with more localized and sparse representations.

However, important limitations are observed. First, SHAP assumes feature independence when estimating marginal contributions, which may produce unrealistic feature combinations. LIME explanations exhibit instability due to their reliance on local sampling, meaning that small perturbations in the neighborhood can alter feature importance rankings. The divergence between SHAP and LIME demonstrates that these methods approximate model behavior rather than reveal true causal relationships.

Counterfactual analysis provides actionable insights by identifying minimal feature changes required to alter predictions. In most cases, reducing prior offenses or charge severity is sufficient to flip outcomes. Importantly, no valid counterfactuals should rely on immutable characteristics such as race or sex; any such instances must be flagged as violations of actionable recourse principles.

From a governance perspective, these findings imply that transparency tools must not be used in isolation. I recommend implementing a formal audit process that includes: (1) cross-method validation (SHAP, LIME, counterfactuals), (2) monitoring for subgroup disparities in error rates, and (3) explicit constraints preventing reliance on immutable or proxy features. Transparency should be treated as a diagnostic tool embedded within ongoing monitoring, rather than a one-time compliance exercise.
