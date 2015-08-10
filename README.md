# Convoy Challenges
## New Feature: Service Suggestions

### Description:

We've just added a Twitter integration in Convoy, which gives us the ability to identify Twitter profiles a user follows that also have a Convoy profile.
So, this challenge is about suggesting new services to our users!

---

## Engineering challenge
The front end team already has a React component that we're going to put in the dashboard in a few places. What we need is a new API end point that simply returns an array of the top 4 suggested services, ranked most relavent to least relavent (relevence defined below).

You are given a list of Convoy users, Twitter users that person follows, and services that user has requested, themselves, on Convoy.
To help users find the most relavent services, we suggest to them services that their Twitter followers have also requested. The services are ranked (1) firstly, by the number of their followers that have ordered them, and (2) secondly, alphabetically.

_Your task is to write a program which finds a list of suggested services for a given user._

Since this is just a protype, and it will be meant for an API endpoint, a simple CLI will suffice that returns an of array of suggested services.

### Input File:

The user service runs a cron job every night at 0800 GMT, pings the Twitter API, and produces a file from the user database as such:
Each line of the file represents one user. The lines are delimited by a colon `:` into four parts: user id, user real name, list of twitter users they follow, and list of services that user has requested. The items in each part are delimited by a comma `,`. Note that some users either don't follow any other Convoy users on Twitter, or have not ordered any services yet.

social_connections.txt
```
1:Ross Perot:Taylor Swift,Mitt Romney,Beyonce,Robert Plant:HP Laser Printer Setup,Nest Thermostat Setup,iCloud Photo Training
2:Barack Obama:Jon Stewart,Beyonce,Ross Perot,Lana Del Ray:iPad Setup,Tractor Feed Printer Lubrication,Nest Thermostat Setup
3:Lana Del Ray:Beyonce,Barack Obama,Jon Stewart:Tractor Feed Printer Lubrication,iPad Setup,HP Laser Printer Setup
4:Robert Plant:Lana Del Ray,Barack Obama,Bono,John Bonham:iPad Setup,Garage Band Training,iCloud Photo Training
5:Mitt Romney:John Bonham,Robert Plant,Ross Perot:
6:Erwin Schrodinger:David Bohm,Linus Pauling,Richard Feynman,Bill Nye the Science Guy:iPad Setup,Lamda Physik Dye Laser Training,Tractor Feed Printer Lubrication
7:John Bonham::Garage Band Training
8:Taylor Swift:Lana Del Ray,Beyonce,Elon Musk:Garage Band Training,iCloud Photo Training
9:Beyonce:Lana Del Ray,Taylor Swift,Bono,Eric Clapton:Galaxy S5 Training,Netflix Setup and Training,Nest Thermostat Setup
10:Jon Stewart:Lana Del Ray,Beyonce,Elon Musk,Bono,Eric Clapton,Taylor Swift,Barack Obama,Tim Cook:iCloud Photo Training
```

### Example Solution CLI

Node.js sample for user id `3` *Feel free to code this in any language of your choice*
```
$ node social_suggestions 1
```

Sample return
```
["Garage Band Training", "iCloud Photo Training", "Nest Thermostat Setup", "Galaxy S5 Training"]
```

### Constraints

1. There can be users that don't follow any other Convoy users.
1. Relationships between users are not necessarily mutual. For example, User A may follow user B, but user B may not follow user A.
1. The text files of social connections can have up to 1000 lines.
1. The same service should never be returned twice in the array.
1. The array should contain four suggested services, or less.

### Solutions to date

**Node.js Solution** [*@scotthasbrouck*](https://github.com/scotthasbrouck)

```
$ node social_suggestions 1
```

**Python Solution** [*@jonoleson*](https://github.com/jonoleson)

```
python social_suggestions 1
```

---

## Design Challenge

Given the API and Twitter integration described above, your task is to design the UI for the React component that will be used ubiqitously across the Convoy platform. The component should be responsive, as it will be used in our mobile apps, and on all desktop environments.

Deliverables:
- Screen shot of a hand drawn simple sketch of the component in a variety of environments.
- The HTML for your design: A single `<div>` element, with any required child elements for your design
- The CSS that implements your design, with the primary brand colors: `#8ed700`, `#84c800`, and `#76b7e4`

Since this will be turned into a React component, submit the final UI as a single `html` file, with all the required styles in the `<head>`. You are free to use any CSS or HTML libraries or preprocessors you like, or staright up vanilla CSS/HTML. But don't worry about JS, or JS animations.

---

## Submission

For any portion of your project that requires a computer and text files, make a pull request from a fork this repo, and include a commit history with comments.

**Remember**! The goal here is not perfection, but to see how you think through a problem and come to an interesting solution.

Happy hacking.
