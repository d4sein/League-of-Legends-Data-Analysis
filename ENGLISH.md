## Overview  

The most noticeable aspect of League of Legends is its competitive nature. People want to get better and rank up, but it's not easy to find the right strategies; or to know which items are best against specific champions or compositions.  

In that regard, Data Analysis can help us understand the value of certain objetives, and how important it is to build counter items when against champions like Nasus and Vladimir.  

## Approach  

The ideia was to use Riot's API and gather matches from all platforms and ranks, adding up to around 180.000 games, then parse all that data to analyse later on. Everything would be saved into a mongoDB file, as it was just easier overall.  

I wrote two scripts for that and they can be found in this repository.   

Also, the data were collected during the 10.9 patch.  

## Results

#### Rift Herald
Underestimated, the first Rift Herald increases the win rate to 63%, and in cases where the team captures both Heralds, the chances of winning go up to 74%. Of course, that doesn't take into account how ahead they were, but it shows that it is an important objetive nonetheless.  

#### Itemization
Itemization is not only a way to increase your strengths, but also a counter action to weaken the enemy team. There's always a teammate to spam *Morellonomicon* when Vladimir gets a kill, and that's for a reason, the global win rate against Vlad is 50%, but when we get only matches where no anti-healing items have been built, it actually goes down to 24%, and it's worse for Nasus, with only 20% win rate.  

This is only considering items tho, so keep in mind abilities like Katarina ultimate or *Ignite* will serve the purpose as well.  

Apart from counter items, there are ways to maximize your champion's capabilities, like *Attack Speed* on Jax, or *Magic Penetration* on Elise. These options work well for them because Jax is a basic attack based champion, which means his damage comes mostly from basic attacks, and for Elise, she is a burst early game champion, she has tons of base damage, but doesn't scale well with *AP (Ability Power)*, so having that penetration is more effective.  

Some champions allow you to have a more freestyle *build path*, but some don't, which is the case of Fiddlesticks. Fiddle has a powerful ultimate for teamfights, but it's useless if you die right after ulting, so building *Zhonya's Hourglass* is a must, as it lets you ult and stay there safely until your team does the clean up.  

In matter of numbers, Fiddlesticks has a 51% win rate globally, but when you isolate the games where no *Hourglass* has been built, it goes down to 42%, solidifying the thesis.  

Some extra info I found was that Trundle *Jungle* into *Warrior* has a 49% win rate, 4% less compared to Trundle Jungle into *Cinderhulk*, with 53%. Warrior is probably a situational pick for carries, whereas Cinderhulk is a much safer option. This also backs up the fact that Trundle scales better with *HP (Health Points)* rather than *AD (Attack Damage)*.  

And finally, when trying to find correlations between champions with related identities, I noticed all these champs: Jax, Renekton, Vayne, Kalista and Twitch, have *Blade of the Ruined* King in their top 5 built items, showing that *BORK* is very powerful (maybe a little overtuned) for basic attack based champions. Something similar happens for mages too, they all go for *Sorcerer's Shoes*, which is.. not that surprising, but helps reinforce what we already know.  

#### Runes
This topic is a bit troublesome to analyse, since runes are heavy dependant on team composition and game plan, that is, you can play the same champion with different runes based on the circumstances. We can filter matches with a set of parameters, which allow us to have much safer results.  

I'm also going to refrain myself from explaining each rune or perk, as some of them are quite extensive.  

For example, Kayn has a 56% win rate with *Conqueror* + *Black Cleaver*, this way we can assume he is most likely playing Red Kayn, otherwise, if only considering runes, we might get a distorted result, with a 49% wr. Also, Kayn with *Electrocute* + *Boots of Mobility* has a 53% win rate, 1% higher than Kayn with *Dark Harvest* + Boots of Mobility, with 52%. That is expected, since Red Kayn is more forgiving, and Electrocute is very straight forward, whereas Dark Harvest relies on game knowledge to be effective.  

Another compelling build we may not expect is Kha'Zix going Conqueror + Black Cleaver in situations where the enemy team is relatively tanky. To get this result I had to filter matches with 3 parameters: first and most obvious, only Conqueror; second, only games where Black Cleaver had been built, since it's a core item for bruisers; third, the enemy team should have at least 2 champions out of a list, where I included champs like Jax, Darius, Garen, Aatrox, Hecarim, Kled, etc. Interestingly enough, Kha'Zix performs very well on this set up, with a 52% win rate.  

For last observations on this topic, we can take a look at how efficient certain perks are in general, and if they synergize well with specific champions.  

*Ravenous Hunter* has a mean of 2% heal from damage dealt, 0.5% above the base stats, but 7 times smaller than the cap at 14%. It gets a little better for Elise and Kha'Zix, with 3% and 3.2%, respectively.  

*Waterwalking* is one of the favorite perks for junglers, with 17.5% activation time for that lane, and 16% overall. Definately worth taking a look into it.  

## Conclusion

This analysis is an attempt to increase the understanding of the game fundamentals in order to maximize win rate. Selecting a champion, building an item, going for an objective, all of those things should be done with a plan in mind.  
