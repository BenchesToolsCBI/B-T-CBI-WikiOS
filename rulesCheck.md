Rules Check
=======

---
Scope
---
Rules Check is a Jenkins project used to assure the right coding of Test Case language.

```
http://jenkins:8080/job/GentestNG_Build/
```

![image_v3BuildChoice][v3BuildChoice]


GentestNG_Build is a jenkins pipeline with 4 stages which will be run consecutively.

A glimpse of the stages:

![image_v3BuildProjectStages][v3BuildProjectStages]

However each stage can be carried out differently according to the development branch:

|     Stages      |                From a trunk development                                 |                     From a branch development                        |
| --------------- | -----------------------------------------------------------             | -------------------------------------------------------------------- |
|Checkout         |Check out from a **trunk** branch development                            |Check out from a **branch** development                                   |
|Build Gentest    |The Gentest application version **need to be defined in the jenkinsfile**|The Gentest application version is systematically defined according to the **BAT ticket number**|
|Buid RT          |The RT application version **need to be defined in the jenkinsfile**     |The RT application version is systematically defined according to the **BAT ticket number**|
|Post build action|The build application is **committed in the trunk** branch               |The build application is compressed and archived in **jenkins artifacts** |



Building Gentest application
----------

Depending on the development branch, the gentest application build is different.

- **From a branch development**:

	* The Gentest application version is based on the bat number (e.g. bat_313 => 0.313.0.0)
	* The Gentest application is compressed and archived in jenkins artifacts. (The bin folder is compressed in gentest.zip and archived in jenkins artifacts)

![image_v3BuildVersion][v3BuildVersion]

Note: The Gentest application version **can not be changed** from a branch development because it is only defined from the bat number.

- **From a trunk development**:

	* The Gentest application version is defined in the jenkinsfile.
	* Gentest application is committed in the [trunk](http://svn/svn/Benches_Tools/GentestNextGen/trunk/GTNG/Builds/gentest).

![image_v3BuildJenkinsfile][v3BuildJenkinsfile]

Note: The gentest version number **should be manually changed** from the jenkinsfile in the trunk.


Building RT_gentest target application
----------

Depending on the development branch, the RT_gentest application version is different.

- **From a branch development**:

	* The RT_gentest application version is defined according to the **bat number**. (e.g. bat_313 => 0.313.0.0)
	* The RT application is compressed and archived in **jenkins artifacts**. (e.g 0.313.0.0 folder is compressed in RT_Desktop_Target.zip and archived in jenkins artifacts)  

![image_v3BuildRT][v3BuildRT]

Note: The RT application version **can not be changed** from a branch development because it is only defined from the bat number.


- **From a trunk development**:

	* The RT application version is defined in the **jenkinsfile**.
	* RT application **is committed** in the [trunk](http://svn/svn/Benches_Tools/GentestNextGen/trunk/GTNG/Builds/gentest/RT%20Desktop%20Target).

![image_v3BuildJenkinsfileRT][v3BuildJenkinsfileRT]

Note: The RT version number **should be manually changed** from the jenkinsfile in the trunk.


[v3BuildChoice]: http://svn/svn/Benches_Tools/Wiki/images/v3BuildChoice.png
[v3BuildProjectStages]: http://svn/svn/Benches_Tools/Wiki/images/v3BuildProjectStages.png
[v3BuildJenkinsfileRT]: http://svn/svn/Benches_Tools/Wiki/images/v3BuildJenkinsfileRT.png
[v3BuildRT]: http://svn/svn/Benches_Tools/Wiki/images/v3BuildRT.png
[v3BuildJenkinsfile]: http://svn/svn/Benches_Tools/Wiki/images/v3BuildJenkinsfile.png
[v3BuildVersion]: http://svn/svn/Benches_Tools/Wiki/images/v3BuildVersion.png
