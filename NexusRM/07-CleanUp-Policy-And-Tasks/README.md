# Create a CleanUp Polices. 

## Step 1: Login with Admin User

## Step 2: Go to Settings Tab -> Repository -> Cleanup Polices -> Create CleanUp Policy

-> Name  : maven-snapshot-cleanup-policy
-> Format: maven2
-> Component Age: 10 
-> Component Usage : 10
-> Release Type:  Pre-Release/Snapshot Versions

## Step 3: Preview Repository 

-> Select [maven-snapshot] -> Click on Preview 

-> It will display all the artifacts which can be delete when the policy excuted. 

## Step 4: Save the Policy. 

## Step 5: Attache the policy to existing repos. 
-> Go to Settings Tab -> Repository -> maven-snapshots -> settings -> cleanup polices -> select newly created policy & Move to Applied Section. -> Save. 

## Setp 6: Now default admin clean up task will take care of housekeeping of all the repos based on clean up policy settings. 



# Tasks

## Step 1 : Go to Settings Tab -> System -> Tasks -> Create Task
-> Type : Maven - Delete SNAPSHOT
-> Task Name: cleanup-snapshot
-> Repository : maven-snapshots
-> Minimum SnapShot Count : 1 
-> Retentions : 30 Days
-> Task Frequency: Weekly
-> Start Date : 08/28/2023
-> Time to run this task : 10:00 
-> Days to run this task : Sunday 
-> Create Tasks 




