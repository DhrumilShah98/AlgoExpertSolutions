# Tournament Winner

## Problem

There's an algorithms tournament taking place in which teams of programmers compete against each other to solve algorithmic problems as fast as possible. Teams compete in a round robin, where each team faces off against all other teams. Only two teams compete against each other at a time, and for each competition, one team is designated the home team, while the other team is the away team. In each competition there's always one winner and one loser; there are no ties. A team receives `3` points if it wins and `0` points if it loses. The winner of the tournament is the team that receives the most amount of points.

Given an array of pairs representing the teams that have competed against each other and an array containing the results of each competition, write a function that returns the winner of the tournament. The input arrays are named `competitions` and `results` respectively. The `competitions` array has elements in the form of `[homeTeam, awayTeam]` , where each team is a string of at most 30 characters representing the name of the team. The `results` array contains information about the winner of each corresponding competition in the `competitions` array. Specifically, `results[i]` denotes the winner of `competitions[i]`, where a `1` in the results array means that the home team in the corresponding competition won and a `0` means that the away team won.

It's guaranteed that exactly one team will win the tournament and that each team will compete against all other teams exactly once. It's also guaranteed that the tournament will always have at least two teams.

Sample Input

```
competitions = [
  ["HTML", "C#"],
  ["C#", "Python"],
  ["Python", "HTML"],
]
results = [0, 0, 1]
```

Sample Output

```
Python
```

#

## Approach 1: Single Pass with Hashtable

```JAVA
import java.util.ArrayList;
import java.util.Hashtable;

class Program {
  /**
  * Approach 1: Single Pass with Hashtable
  *
  * Time Complexity: O(N), where N is total number of competitions.
  * Space Complexity: O(K), where K is total number of teams.
  *
  * @param competitions  array list of competitions.
  * @param results  array list of results.
  */
  public String tournamentWinner(ArrayList<ArrayList<String>> competitions,
                                 ArrayList<Integer> results) {
    Hashtable<String, Integer> teamsScore = new Hashtable<String, Integer>();
    String winnerTeam = "";
    int winnerTeamScore = -1;
    for(int i = 0; i < competitions.size(); ++i) {
      String currentWinningTeam = competitions.get(i).get(results.get(i) == 1 ? 0 : 1);
      int currentWinningTeamScore = teamsScore.getOrDefault(currentWinningTeam, 0) + 3;
      teamsScore.put(currentWinningTeam, currentWinningTeamScore);
      if(currentWinningTeamScore > winnerTeamScore) {
        winnerTeam = currentWinningTeam;
        winnerTeamScore = currentWinningTeamScore;
      }
    }
    return winnerTeam;
  }
}

```

### Complexity Analysis

- Time Complexity: O(N), where N is total number of competitions.
- Space Complexity: O(K), where K is total number of teams.
