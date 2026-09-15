---
title: "Multiple Columns with Redis Sorted Set"
author: "Ricardo Ferreira"
tags:
  - "golang"
  - "Multiple Columns"
  - "Redis"
  - "Sorted Set"
categories:
  - "Redis"
date: 2020-03-03
nolastmod: true
draft: false
---
Recently I had to build an application that would store and order players in a [Redis Sorted Set](https://redis.io/commands#sorted_set), but using multiple columns as criteria for the score, instead of just one. After trying to find a proper solution on the web and failing to do so; I decided to put my head to work and figure out an way. This post will show how did I accomplished that.

![](sorted-set-with-redis-v1.png)

It turns out that my application has players with the following fields:

  * **Score** : which is the total number of points received.
  * **Level** : which reveals how hard is being the game.
  * **Losses** : The number of times the player game-over.

I would like to order players using these fields as criteria, specifically using the following order:

  1. **First by score**. This is the default ordering. Players with higher scores would come first.
  2. **Then by level**. Players with the same score but with a higher level would come first.
  3. **Then by losses**. Players with the same score and level but with less losses would come first.

As you can see here, not only I need to use multiple columns as ordering criteria, but the columns also mix-and-match in terms of ascending and descending. The ordering for the 'score' and 'level' fields would be ascending, as the order for the 'losses' field would be descending.

The trick here is to come up with a single value that would encapsulate all this logic. Redis only accepts one number as parameter so there is no actual way to use them all. With that in mind, I decided to use the following formula:
```
finalScore = (score + level) - losses
```

In which I would have to compute before writing the data into Redis. Here is an example of this using Go:
```
func addPlayerToRedis(player *Player) {
  cache.Do("ZADD", "scoreboard", score(player), player.ID)
}

func score(player *Player) int {
  return (player.Score + player.Level) - player.Losses
}
```

That did the trick like a charm. I honestly don't know if this is the best way to do this (feedback is more than welcome) but it helped me to implement the application. I do hope that helps you too.
