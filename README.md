# fn-list-objects
A Java function that interacts with OCI Object Store to list objects using
 Resource Principals.

Included files for both Java 11 and Java 8:
* Java 11 - use `func.yaml` and `pom.xml`
* Java 8 - rename `func-jdk8.yaml` to `func.yaml` and `pom-jdk8.xml` to `pom
.xml`


## Dynamic group
Create a dynamic group for your compartment as shown below. Use your
 compartment OCID.

![](images/userinput.png)
>```
> Name: <dg-name>
> Matching Rules:
> ALL {resource.type = 'fnfunc', resource.compartment.id = '<your-compartment-OCID>'}
>```

Note: You can also create dynamic groups based on Function OCID or Tags

## Policy to give access to the dynamic group 
Create a policy to allow your function to read objects from your storage bucket.
Create a policy to give access to the your dynamic group. Use your
 dynamic group name, compartment name and bucket name:

![](images/userinput.png)
>```
> Name: dg-policy
> Policy Statement:
> allow dynamic-group <dg-name> to inspect objects in compartment <compartment-name> where target.bucket.name='<bucket-name>'
>```
