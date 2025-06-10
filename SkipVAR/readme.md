# Model Files

This folder contains trained decision model files with different SSIM thresholds.

## Model List

*   **decison_models_ssim_88:** Models trained with SSIM threshold of 0.88.
*   **decision_model_ssim_86:** Models trained with SSIM threshold of 0.86.
*   **decision_model_ssim_84:** Models trained with SSIM threshold of 0.84.
*   **decision_model_ssim_84_diff_only:** Models trained with SSIM threshold of 0.84, **but only accepts [HF_Diff] as input**.

## How to Use

To use these models, you need to modify the model path in the `Infinity.py` file.

1.  Open the `Infinity.py` file.
2.  Locate lines 286.
3.  Replace the placeholder path(s) on these lines with the path to the desired model file (e.g., `self.decision_models_folder='./SkipVAR'+'decision_model_ssim_84'`).
4.  Ensure the model you select matches the input data you intend to use (especially for `decision_model_ssim_84_diff_only`).