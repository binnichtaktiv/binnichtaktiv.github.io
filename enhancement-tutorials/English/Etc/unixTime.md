# Unix Time

## What is `Unix Time`? -`Wikipedia`


`Unix time` is a date and time representation widely used in computing. It measures time by the number of `seconds` that have `elapsed` since 00:00:00 UTC on 1 January 1970, the Unix epoch, without adjustments made because of leap seconds.

Read more [here](https://en.wikipedia.org/wiki/Unix_time)



### How is it used when making scripts?

In scripts, you might see `expiration-date` or `purchase-date` which is followed by what it seems like random numbers.

E.G.:

```

{
    // script
    // more of the script
    purchase-date: 1706809093, <-- Thursday, February 1, 2024 5:38:13 PM
    expiration-date: 4073650693 <-- Sunday, February 1, 2099 5:38:13 PM
}

```

You can use [this](https://www.epochconverter.com/) website to convert between `human date` & `Unix/Epoch Timestamp` 
