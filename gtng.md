GTNG
=======
GTNG refers to Gentest Next Generation, also known as Gentest V3.
...

![image_GTNG_icon][GTNG_icon]


Architecture
----------

Please see [this file](http://svn/svn/Benches_Tools/Wiki/SIL_HILe_Technical_Architecture.pptx).


Source code & Build artifect
----------

The [trunk](http://svn/svn/Benches_Tools/GentestNextGen/trunk) consists of GTNG and SIL_WS:
```
http://svn/svn/Benches_Tools/GentestNextGen/trunk
```

**GTNG** regroups the Gentest app source and RT target source.

**SIL_WS** can be considered as a permament branch of SIL source. See [SIL]() page for more details.

The latest build of Gentest is in the [Builds](http://svn/svn/Benches_Tools/GentestNextGen/trunk/GTNG/Builds/gentest) folder. In which, there are build artifacts of [RT target](http://svn/svn/Benches_Tools/GentestNextGen/trunk/GTNG/Builds/gentest/RT Desktop Target/RT_Gentest).
See more details of each folder in [GentestNG Build Folder Architecture](gtngBuildFolder.md) page.

There exists a Jenkins project to build Gentest & RT target applications: [GentestNG_Build](http://jenkins:8080/job/GentestNG_Build/)
See more details in [GentestNG_Build](gtngBuild.md) page.


Dev Instructions
----------
- Create new algorithm to control test bench actuator

When we want to control an APB MI brake, we can use the **PLCMOC** algorithm and its apply/release actions (PLCMOCON/PLCMOCOFF). See more Actions in [GTNG Syntax](http://svn.fbrakes.com/svn/RD_Global_Activities/On_Going/RD_4000_Tools_management/RD_4100_Tools_storage/29-Gentest/UserDocCenter/index.html#!v3syntax.md#Actions).
But the creation of new ones is possible. For that, there is some files to modify in addition of creating the algorithm C file and its dependencies.

For example, when we want to control an **APB DI** brake with some more parameters than MI brake, we created a **PLCAPB** algorithm and its apply/release actions (PLCAPBON/PLCAPBOFF).
Check tutorial for [how to integrate new algorithm to pilot test bench actuator](tuto_addAlgo.md).


Validation
----------
- [SIL_WS Validation](gtngValidationSILWS.md)
- [GTNG + SIL_WS Validation](gtngValidationFull.md)


StandAlone
----------
As a a variant of Gentest V3, **StandAlone Mode** can select and run TestCases with or **WITHOUT** Gentest computer, as long as it is properly configured.

To switch from nominal V3 mode to StandAlone mode, see [StandAlone Checklist](v3checklist_standAlone.md) page.


Note: Maybe it will be better to develop a simple GUI interface to facilitate the TestCase compile & transfer between users and RT target.

See [Architecture](gtngArchitecture.md) page for design details.



Syntax
----------
[V3 syntax](http://svn.fbrakes.com/svn/RD_Global_Activities/On_Going/RD_4000_Tools_management/RD_4100_Tools_storage/29-Gentest/UserDocCenter/index.html#!v3syntax.md) is documented in the **User Doc Center**:
```
http://svn.fbrakes.com/svn/RD_Global_Activities/On_Going/RD_4000_Tools_management/RD_4100_Tools_storage/29-Gentest/UserDocCenter/index.html#!v3syntax.md
```



[GTNG_icon]: http://svn/svn/Benches_Tools/Wiki/images/GTNG_icon.ico

