## DSA Mini project 

### General idea
Declare a struct person array that contains a vector of pairings of persons the person meets and the day they meet, as well as information about their present location, current status, and, if relevant, the day they tested positive. would be initialised to -1 by default.

 A person's entry in the meet array will be erased if their meet date is more than 14 days in the past since their status won't change.


 Depending on the day and the supplied data, update the status, station, and meet vector.

 To compute the safety values (choose the top three) and apply Dijkstra to identify the shortest path, keep the stations as graphs (mostly for q2).

 For the individual who indices, indexing begins at zero (information for the user providing inputs).

 ### Q1 specific 
 People who TESTED positive on that day D are on List L.

We need to look for that person's primary and backup contacts for the previous X days.

On list L, no one has moved from their station in 14 days. They remain in their present station (i.e., the location where they tested positive). Run a check in q2 to see if the individual who is being requested to go is currently quarantined. If so, display an error notice.

 For job 1, list L is required.

- On day D.

- X value (Amount of days to look back on)

- The total number of positive tests that day.

- Information about those who tested positive.

 Following a 14-day quarantine, we expect those who tested positive to turn negative. The primary and secondary contacts, on the other hand, will remain as they are, because they could be asymptomatic carriers.
### Q2 specific

 We will use the danger values as weights for the edges to find the safest paths using Dijkstra's algorithm.

 The first run will give us the safest path, for the second run, we remove the HEAVIEST edge in path 1 (which is the most dangerous) and run dijkstra again.

 This continues, till we find 3 paths (if exists).

 We are using directed edges between stations to account for the different danger values. For example, an edge FROM A TO B has the danger value of B as a weight, and FROM B TO A has the danger value of A as the weight.

 Once we find the three safest paths, we calculate their distances and rank them accordingly (Highest safety first, in case of same safety, sort by distance).

 We then take input for the user's choice, 0 for not going, 1 for path 1, 2 for path 2 (If exists) and so on.

 We update the person's status and current station accordingly. We also keep adding the people he meets on the way to the meet vector. His/her previous station struct and all the stations he/she encounters on his/her chosen path will also be updated (because the danger value and number of residents will change as well). (The stations on the path will only have to be updated if the person is a primary contact, all other cases will not make a difference).

### Q3 specific

 We will create a menu driven code for this, which accepts a person's index and the query, and fucntions accordingly



### Q3 p1 (status)
input format: 
    int DAY , int INDEX  
Output format: 
    string representing the status of the person of index "INDEX" on day "DAY"

Note: DAY should not be less than the status alloted day

### Pseudocode p1
```c++
 access index of that person, in array
 cout<<status<<;
```
### Q3 p2 (location)
input format: 
    int INDEX
Output format:
    int current_station of the person with index "INDEX"

### Pseudocode p2
```c++
 access index of person
 cout<<cur_station;
```
### Q3 p3  (info regarding persons in a station )
input format:
    int DAY , int STATION_NUM
output format:
    list of the [positive , primaryContact , secondaryContact , Negative] persons in the station "STATION_NUM"  in order 

NOTE: DAY should not be less than the status alloted day

### Pseudocode p3
```c++
person* list;
 for(in person array)
 {
    if(in the station)
    {
        Add to list ;

    }
 }
    qsort ( list);
printf ( list ) ; 

 ```
