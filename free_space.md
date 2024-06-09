# Space utilization recipes

## Cache volumes

A quick/dirty way to see cache volumes, the total utilization and how much
space is remaining.

`# df -h | grep /cache | awk '{print $NF, $(NF-1), $(NF-2)}'`

```text
/cache0 73% 2.8T
/cache1 81% 1.9T
/cache2 75% 2.6T
/cache3 89% 1.2T
```
