.. _usecases:

NStack Uses
===========

Productionising Models
**********************
Productionise your models in the cloud without complex engineering, where they can be used in workflows and attached to data-sources. For instance, you can build a Random Forest classifier locally in Python, publish it to your cloud provider, and connect it to a streaming system, database, data-lake, or HTTP endpoint in under 10 minutes.


Data Integration
****************

Transform disparate and disconnected data-sources -- such as 3rd-party APIs, legacy infrastructure, or databases into streams of typed, structured records -- which can be composed together. For instance, you could set up a workflow in the cloud which pipes the Twitter Ads API into your data-lake (and even do some modelling in Python in-transit) in under 5 minutes.


Software Lifecycle
******************

NStack provides best practices from software engineering and end-to-end software life-cycle management to the data science process, including,

* **sharing and reuse** - build and deploy individual model modules to your cloud that can reused, imported, and utilised by other members, either within your team or by third-parties
* **reproducibility** - build models with guaranteed versions of system and language dependencies, that can then be shared with confidence that your code is bit-for-bit identical everywhere
* **versioning** - modules a have a immutable, globally unique, version - so when importing to use in a workflow, you can be sure the API, code, and artifacts are just as you intended, allowing you to upgrade to newer versions when ready 
* **runtime isolation** - all modules in your workflow run using our container technology, meaning they are fully isolated from each other, can scale up as needed, and won't interfere with each others data

