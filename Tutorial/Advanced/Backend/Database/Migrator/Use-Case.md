# Init

**No need to do anything.**

When creating a migrate branch, cicd will automatically create a set of databases based on the branch name.

# Migrate

## Center

For the Center.DatabaseCreate and Center.DatabaseCreate.Partner10000 parts, sql scripts should not be added/deleted/modified. If you need to update, you should make corresponding changes by writing migrate files .

For the Center.Register part, each time a version is released, you need to add/delete/modify the corresponding sql scripts according to the actual situation to ensure that the newly registered partner uses the latest script. At the same time, write the migrate file to upgrade the existing partner.

### upgrade

1. If it involves changes to Center.Register, add/delete/modify the corresponding script.

2. Confirm version number and write the corresponding migrate file, see [Migration](/Tutorial/Advanced/Backend/Database/Migrator/Migration) for detail.

3. Push the changes to git, wait for the ci cd process to automatically test and automatically package the nuget package. 

4. Registration service update nuget package version and release.

5. Prepare a job for upgrading, which is used to perform database upgrade operations. For a detailed description of the job, see [Jobs](/Tutorial/Advanced/Backend/Database/Migrator/Jobs#gitlab-ci.yml). 

6. Modify .gitlab-ci.yaml, submit it to the code base, and the cicd process will automatically execute the job. Test whether the database has been changed correctly as required. For changes in .gitlab-ci.yaml, see [gitlab-ci.yml](/Tutorial/Advanced/Backend/Database/Migrator/Jobs#gitlab-ci.yml). 

7. Prepare the job and the image used to execute the job, Release.

### downgrade

1. If it involves changes to Center.Register, rollback sql script changes. 

2. Registration service/synchronization relocation service downgrade nuget package version and release.

3. Prepare a job for downgrade, which is used to perform database downgrade operations. For a detailed description of the job, see [Jobs](/Tutorial/Advanced/Backend/Database/Migrator/Jobs). 

4. Modify .gitlab-ci.yaml, submit it to the code base, and the cicd process will automatically execute the job. Test whether the database has been changed correctly as required. For changes in .gitlab-ci.yaml, see [gitlab-ci.yml](/Tutorial/Advanced/Backend/Database/Migrator/Jobs#gitlab-ci.yml). 
5. Prepare the job and the image used to execute the job, Release.

6. After downgrade, delete the migrate file. Even if the migrate file will be used in the future, it should be deleted first, rewritten when it is used, and the version number must be re-determined. 

## Platform

## Queue, File, configuration.general, reporting.general

Note: Do not add/delete/modify sql scripts !!!

### upgrade

1. Confirm version number and write the corresponding migrate file, be careful not to add/delete/modify sql scripts. For a detailed description of the migrate file, see [Migration](/Tutorial/Advanced/Backend/Database/Migrator/Migration). 

2. Prepare a job for upgrading, which is used to perform database upgrade operations. For a detailed description of the job, see [Jobs](/Tutorial/Advanced/Backend/Database/Migrator/Jobs). 

3. Modify .gitlab-ci.yaml, submit it to the code base, and the cicd process will automatically execute the job. Test whether the database has been changed correctly as required. For changes in .gitlab-ci.yaml, see [gitlab-ci.yml](/Tutorial/Advanced/Backend/Database/Migrator/Jobs#gitlab-ci.yml). 

4. Prepare the job and the image used to execute the job, Release.

### downgrade 

1. Prepare a job for downgrade, which is used to perform database downgrade operations. For a detailed description of the job, see [Jobs](/Tutorial/Advanced/Backend/Database/Migrator/Jobs). 

2. Release and prepare image to excute job.

3. After downgrade, delete the migrate file. Even if the migrate file will be used in the future, it should be deleted first, rewritten when it is used, and the version number must be re-determined. 

## configuration.site, reporting.site

Note: When the version is released, you need to add/delete/modify the corresponding sql scripts according to the actual situation to ensure that the newly registered site uses the latest scripts.
At the same time write the migrate file to upgrade the existing site.

### upgrade

1. Confirm version number, add/delete/modify corresponding sql scripts and write corresponding migrate files. For a detailed description of the migrate file, see [Migration](/Tutorial/Advanced/Backend/Database/Migrator/Migration). 

2. Push the changes to git, wait for the ci cd process to automatically test and automatically package the nuget package. 

3. Registration service/synchronization relocation service update nuget package version and release.

4. Prepare a job for upgrading, which is used to perform database upgrade operations. For a detailed description of the job, see [Jobs](/Tutorial/Advanced/Backend/Database/Migrator/Jobs). 

5. Modify .gitlab-ci.yaml, submit it to the code base, and the cicd process will automatically execute the job. Test whether the database has been changed correctly as required. For changes in .gitlab-ci.yaml, see [gitlab-ci.yml](/Tutorial/Advanced/Backend/Database/Migrator/Jobs#gitlab-ci.yml). 

5. Prepare the job and the image used to execute the job, Release.

### downgrade 

1. Rollback sql script changes.

2. Registration service/synchronization relocation service downgrade nuget package version and release.

3. Prepare a job for downgrade, which is used to perform database downgrade operations. For a detailed description of the job, see [Jobs](/Tutorial/Advanced/Backend/Database/Migrator/Jobs). 

4. Modify .gitlab-ci.yaml, submit it to the code base, and the cicd process will automatically execute the job. Test whether the database has been changed correctly as required. For changes in .gitlab-ci.yaml, see [gitlab-ci.yml](/Tutorial/Advanced/Backend/Database/Migrator/Jobs#gitlab-ci.yml). 

4. Prepare the job and the image used to execute job, Release.

5. After downgrade, delete the migrate file. Even if the migrate file will be used in the future, it should be deleted first, rewritten when it is used, and the version number must be re-determined. 

## configuration.fulltextindex, reporting.fulltextindex

Note: When the version is released, you need to add/delete/modify the corresponding sql scripts according to the actual situation, to ensure that when creating a new site library, the latest script is executed in the fulltextindex library.

At the same time, the migrate file is written to upgrade the table corresponding to the existing site library. 

### upgrade

1. Confirm version number, add/delete/modify corresponding sql scripts and write corresponding migrate files. For a detailed description of the migrate file, see [Migration](/Tutorial/Advanced/Backend/Database/Migrator/Migration). 

2. Push the changes to git, wait for the ci cd process to automatically test and automatically package the nuget package. 

3. Registration service/synchronization relocation service update nuget package version and release.

4. Prepare a job for upgrading, which is used to perform database upgrade operations. For a detailed description of the job, see [Jobs](/Tutorial/Advanced/Backend/Database/Migrator/Jobs). 

4. Modify .gitlab-ci.yaml, submit it to the code base, and the cicd process will automatically execute the job. Test whether the database has been changed correctly as required. For changes in .gitlab-ci.yaml, see [gitlab-ci.yml](/Tutorial/Advanced/Backend/Database/Migrator/Jobs#gitlab-ci.yml). 

5. Prepare the job and the image used to execute the job, Release.

### downgrade 

1. Rollback sql script changes.

2. Registration service/synchronization relocation service downgrade nuget package version and release.

3. Prepare a job for downgrade, which is used to perform database downgrade operations. For a detailed description of the job, see [Jobs](/Tutorial/Advanced/Backend/Database/Migrator/Jobs). 

4. Modify .gitlab-ci.yaml, submit it to the code base, and the cicd process will automatically execute the job. Test whether the database has been changed correctly as required. For changes in .gitlab-ci.yaml, see [gitlab-ci.yml](/Tutorial/Advanced/Backend/Database/Migrator/Jobs#gitlab-ci.yml). 

4. Prepare the job and the image used to execute job, Release.

5. After downgrade, delete the migrate file. Even if the migrate file will be used in the future, it should be deleted first, rewritten when it is used, and the version number must be re-determined. 
