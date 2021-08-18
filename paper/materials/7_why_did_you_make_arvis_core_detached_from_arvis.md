# Why did you make arvis-core detached from arvis?

At first, I was planning making Arvis CLI module (which use Ink as framework).

To support CUI and GUI both, I made `arvis-core` which is detached from renderer logic.

But soon I thought it wouldn't be very useful.

So, I decided to discard CLI support.