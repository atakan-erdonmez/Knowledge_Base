---
link:
  - "[[Lambda]]"
---
  
**A layer is a ZIP archive that contains libraries, a custom runtime, or other dependencies**.

You can configure your AWS Lambda function to pull in additional code and content in the form of layers. With layers, you can use libraries in your function **without needing to include them in your deployment package**. Layers let you keep your deployment package small, which makes development easier. A function can use up to 5 layers at a time.

You can create layers, or use layers published by AWS and other AWS customers. Layers support resource-based policies for granting layer usage permissions to specific AWS accounts, AWS Organizations, or all accounts. The total unzipped size of the function and all layers can't exceed the unzipped deployment package size limit of 250 megabytes.