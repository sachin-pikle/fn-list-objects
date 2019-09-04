# fn-list-objects
A function that interacts with OCI Object Store to list objects using Resource 
Principals

## Dynamic group
Create a dynamic group for your compartment as shown below:

![](images/userinput.png)
>```
> Name = dg-compartment-<compartment-name>
> Matching Rules:
> ALL {resource.type = 'fnfunc', resource.compartment.id = 'ocid1.compartment.oc1..aaa...jia'}
>```

Note: You can also create dynamic groups based on Function OCID or Tags

## Policy to give access to the dynamic group 
Create a policy to give access to the above dynamic group:

![](images/userinput.png)
>```
> Name = dg-policy
> Policy Statement:
> allow dynamic-group <dg-name> to inspect objects in compartment <compartment-name> where target.bucket.name='<bucket-name>'
>```
