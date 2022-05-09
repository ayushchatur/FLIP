# FLIP - Federated Learning Interoperability Platform
Complex and predictive patterns can be extracted from large volumes of data to train and validate AI algorithms and ensure they are safe for use in clinical practice. 

Keeping the data inside the Trust firewall - a secure network that protects privacy - is the safest and most effective way to train AI in public health.

Our Federated Learning Interoperability Platform (FLIP) will help link data from multiple NHS Trusts to enable AI at scale. It is comprised of three parts:

## Secure Enclaves
We are building dedicated secure data storage for processing and analysis within each of our partner NHS Trusts – a secure enclave or area within the firewall that keeps sensitive patient data inside the Trust.

Data from across the Trusts’ patient records systems will be transfered into the secure enclave for curating and aggregation, unifying medical imaging scans from Picture Archiving and Communications Systems (PACS, the industry-standard storage system incorporating different medical imaging types) and other electronic health data. 

![FLIP](https://www.aicentre.co.uk/sites/default/files/inline-images/FLIP%20diagram_12%20Nov.png )

The secure enclave is comprised of multiple hardware and software components. 
We use high-performance NVIDIA DGX 1 processers to train our algorithms, which have the computing power to analyse hundreds of thousands of medical imaging scans in minutes. 
XNAT, an open-source image informatics platform that ingests Digital Imaging and Communications in Medicine (DICOM, the industry-standard for medical images and related data) images from PACS, allows us to run our algorithms against automatically anonymised images safely. 

CogStack is used for information retrieval and extraction. The platform can process data from multiple sources and applies Natural Language Processing to make sense of unstructured data and extract data from semantic information. We use CogStack to select participant cohorts for our research. CogStack builds on Elastic Search, for storage and complex queries, while Kibana is the front-end tool clinicians will use.

A secure enclave has been created at partner sites including King’s College Hospital Foundation Trust and Guy’s and St Thomas’ NHS Foundation Trust. 

## Federated learning
AI algorithms need to train on diverse clinical datasets from multiple sources to ensure the resulting model is both reliable and generalizable.

Our federated learning approach brings algorithms to the data within each NHS Trust’s secure enclave, without needing to share information outside the secure firewall or break local governance rules. 

Algorithmic models are sent to multiple Trusts and trained on local data before being securely combined to achieve consensus. The model is then applied within each secure enclave, where it learns from the data, is updated again, and the process repeated until an improved consensus model is created. 

To achieve convergence, the process of learning and combining is reiterated, until each locally applied model reaches the same conclusion, indicating that the model is generalizable and can be consistently applied. 

Interoperability and data harmonisation
Electronic healthcare records are complex and heterogeneous, making it difficult to create interoperable algorithms that can be applied to data that is stored and categorised in different ways across multiple sites. 

To harmonise this heterogeneous data, we use ontological and data interoperability standards to structure the data and make it actionable. When data is standardised and harmonised across multiple hospitals and clinical systems, it is possible for AI algorithms to query, learn and action data via an open standards-based data interface. This consistency makes interoperability possible, allowing researchers to extract valuable insights from multiple data sources.

## How FLIP adds value
Our Federated Learning Interoperability Platform (FLIP) ensures a high level of fidelity in AI output models compared to traditional aggregative data strategies because the data it trains on does not need to be anonymized before use.

FLIP also allows us to adhere to each Trust’s governance and data privacy regulations and ensures that our models are scalable in international contexts in full compliance with international laws and guidance.

FLIP will be deployed across seven NHS Trusts.


