# Solution-to-pod-errors-for-M1-M2-MacBooks.

  For M1-M2 Chip MacBooks, you can compile older projects created without using "Swift Packages" (projects created on the Intel operating system) using these methods.

1) After the podfile is created, instead of entering the "pod install" command from the terminal, you can use the command " rm -rf ~/Library/Caches/CocoaPods; rm -rf Pods; rm -rf ~/Library/Developer/Xcode/DerivedData/*; pod install; ". This command completely clears the cache and installs from scratch.

  



2) There is a compilation error after XCode 14.3.1 and "Ventura 13.4" system update. To solve this, the information written at the bottom needs to be added to the "Podfile" file.

  
    <img width="639" alt="Podfile" src="https://github.com/kaanssss/Solution-to-pod-errors-for-M1-M2-MacBooks./assets/74143983/ca8d7c45-915d-4107-b80c-31134bdcd2d2">


  The last part indicates that the "YourProject" project has set the minimum iOS version to '11.0' and that these configurations will be used during the build process.





3) If there is a problem with the archive process.
   
    <img width="345" alt="Pod" src="https://github.com/kaanssss/Solution-to-pod-errors-for-M1-M2-MacBooks./assets/74143983/5a8747bb-1c3e-4893-a649-bddf01d82d12">

    <img width="1084" alt="PodFramework" src="https://github.com/kaanssss/Solution-to-pod-errors-for-M1-M2-MacBooks./assets/74143983/f603235a-5994-4006-bd6b-6a2dae634eed">

  The change " source="$(readlink -f "${source}")" in the "Pods-YourProject-frameworks" file will eliminate the archive problem.  
Here only the -f command is added next to readlink.





4) Simulator settings.

   <img width="1029" alt="Rosetta" src="https://github.com/kaanssss/Solution-to-pod-errors-for-M1-M2-MacBooks./assets/74143983/79580ada-8433-44f1-b3f4-9b4df94b90ec">


  If the settings are set as shown in Xcode, the build will complete successfully. 

