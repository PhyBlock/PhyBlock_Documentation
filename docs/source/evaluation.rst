Evaluation Workflow
===================

This guide describes the process for evaluating vision-language models (VLMs) on the PhyBlock 3D block assembly benchmark.

Dataset
-------

The dataset is officially released on `HuggingFace <https://huggingface.co/datasets/PhyBlock/PhyBlock_Benchmark>`_.

Standard Evaluation Procedure
-----------------------------

1. Generate Predictions
~~~~~~~~~~~~~~~~~~~~~~~
Use the scripts in ``inference_scripts/`` to generate raw model predictions for all 400 block assembly scenarios.
- Each model should output predictions in JSON format.

2. Evaluate Model Outputs
~~~~~~~~~~~~~~~~~~~~~~~~~
Prepare the following directories:

.. list-table::
   :header-rows: 1

   * - Argument
     - Description
   * - ``--raw_outputs_json_dir``
     - Path to raw model prediction JSON files
   * - ``--matching_json_dir``
     - Candidate block JSONs (see ``data/SCENEs_400_Cand_Jsons``)
   * - ``--groundtruth_json_dir``
     - Ground-truth structure JSONs (see ``data/SCENEs_400_Goal_Jsons``)
   * - ``--extracted_json_dir``
     - Output directory for parsed assembly sequences
   * - ``--results_dir``
     - Directory for evaluation results (CSV/TXT)

Run the evaluation with:

.. code-block:: bash

   python evaluate_block_construction.py

3. Results
~~~~~~~~~~
After evaluation, you will obtain metrics and summary files, such as:

- ``Results_level1.csv``: Level 1 (basic matching)
- ``Results_level234.csv``: Levels 2–4 (complex reasoning)
- ``Results_Levels.txt``: Overall summary

Visualization Examples
----------------------

The following are sample visualizations of model-predicted assembly processes:

.. image:: ../../Imgs/006.gif
   :width: 120px
.. image:: ../../Imgs/007.gif
   :width: 120px
.. image:: ../../Imgs/008.gif
   :width: 120px
.. image:: ../../Imgs/018.gif
   :width: 120px

.. image:: ../../Imgs/029.gif
   :width: 120px
.. image:: ../../Imgs/110.gif
   :width: 120px
.. image:: ../../Imgs/059.gif
   :width: 120px
.. image:: ../../Imgs/089.gif
   :width: 120px

.. note::
   Each animation demonstrates how a model constructs the target block structure step by step.
----

For detailed API documentation and further customization, refer to the script docstrings and in-code comments.
