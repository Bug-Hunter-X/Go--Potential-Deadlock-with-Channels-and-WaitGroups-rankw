# Go: Potential Deadlock with Channels and WaitGroups

This repository demonstrates a potential deadlock scenario in Go using channels and WaitGroups. The program consists of two goroutines: a sender and a receiver. The sender sends five integers to the channel, and the receiver receives and prints them.  A WaitGroup is used to synchronize the goroutines.

The issue arises if the receiver goroutine finishes processing all the received values before the sender goroutine closes the channel. This can result in the sender goroutine blocking indefinitely while attempting to close a channel that no longer has any active receivers. The WaitGroup will prevent the main function from exiting, resulting in a deadlock.

The solution addresses this by ensuring that the channel is always closed after all the values have been sent.