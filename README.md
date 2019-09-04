# fn-list-objects
This example is based on Abhishek Gupta's blog [Getting Started with Oracle Functions and Object Storage](https://blogs.oracle.com/cloud-infrastructure/getting-started-with-oracle-functions-and-object-storage)

A Java function that interacts with OCI Object Storage to list objects using
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

## Deploy your function
Use your app name:

![](images/userinput.png)
>```
> fn -v deploy --app <app-name>
>```

## Invoke your function
Invoke your function. Use your bucket name and app name:

![](images/userinput.png)
>```
> echo -n '<bucket-name>' | fn invoke <app-name> list-objects
>```
