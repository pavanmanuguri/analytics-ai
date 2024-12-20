# Lab 1: Create Identity Resources

## Introduction

Before we can start deploying resources that make up our multimodal RAG pipeline, we will need to create identity resources to give Data Science notebooks access to model deployments, object storage and other resources. This lab will go over all the creating required Groups, Dynamic Groups and Policies. It is recommended that a tenancy administrator complete this lab.

**Note**: You will need to create these resources in your home region.

### Task 1: Find Compartment OCID

1. Open the main "hamburger" menu in the top left corner of the Console. Select "Identity & Security" and then click "Compartments".
![Opening main OCI menu](images/)
2. Click into your desired compartment for model deployment.
3. Copy OCID of your compartment, paste this value into your favorite code editor/notepad. We will use this on the next task.
![Copy compartment OCID](images/)

### Task 2: Create Dynamic Group
1. From the same screen, navigate to Domains.
![Navigate to Domains](images/)
2. Click the Default domain.
![Default domain](images/)
3. Click Dynamic Groups.
![Dynamic Groups navigation](images/)
4. Click Create Dynamic Group.
![Create dynamic group](images/)
5. Enter the following:
- Name: data-science-dynamic-group
- Description: Data Science dynamic group
![Name dynamic group](images/)
6. In the Matching Rules section, click Match any rules defined below.
![Match any rules defined below](images/)
7. Under "Rule 1", enter the following:
```
<copy>
ALL {resource.type='datasciencenotebooksession', resource.compartment.id='<compartment-ocid>'}
</copy>
```

**Note**: Replace **<compartment-ocid>** with your compartment OCID that was stored in your notepad in Task 1.

![Create first rule](images/)
8. Click Additional Rule.
![Additional rule](images/)
9. Under "Rule 2", enter the following:
```
<copy>
ALL {resource.type='datasciencemodeldeployment', resource.compartment.id='<compartment-ocid>'}
</copy>
```

**Note**: Replace **<compartment-ocid>** with your compartment OCID that was stored in your notepad in Task 1.

10. Click Additional Rule.
![Additional rule 2](images/)
11. Under "Rule 3", enter the following:
```
<copy>
ALL {resource.type='datasciencejobrun', resource.compartment.id='<compartment-ocid>'}
</copy>
```

**Note**: Replace **<compartment-ocid>** with your compartment OCID that was stored in your notepad in Task 1.
12. Click Create.
![Create dynamic group](images/)

### Task 3: Create Policies
1. Open the main "hamburger" menu in the top left corner of the Console. Select "Identity & Security" and then click "Policies".
[Navigating to Policies](images/)
