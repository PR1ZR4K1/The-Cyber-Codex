2024/08/31 16:54
Status: #idea
Tags:

# CISO Website Continued

**Next steps for features I need to include before initial release to the club**

- [ ]  *Settings*
	- [x] Ability to view profile and make changes
	- [x] Add new fields ie: isCMP, hasPaidDues, isOfficer, and more
	- [x] Format page for different screen size starting with mobile phones!
- [ ] *Projects*
	- [x] change which methods are used to pull user information.
	- [x] Update participation records to include user authentication token
	- [x] Create way to track project participation
		- [x] participationRecords for each individual project, and for each user.
		- [x] For each project a participation record will be created each time that project's proposed start time occurs. From that point until the end of the project any participants are added to that record.
		- [x] Need a way to derive a documentID that can be created uniquely for each time the project would start. Was thinking data and time would be an easy way to achieve this.
	- [ ] Update state of project participation button based on current time vs project start day and time.
	- [x] Have default user in place for projects without a colead or in cases where information is unable to be pulled from db.
	- [x] Format page for different screen size starting with mobile phones!
	- [ ] View other users currently participating in the project.
- [ ] *Officers*
	- [ ] Add a modal that gets triggered by a click on officer card to display additional information of the officer
	- [x] Add professional pictures for each officer
	- [x] Use data files to handle additional information for now.
	- [ ] Format page for different screen size starting with mobile phones!
- [ ] *Events*
	- [x] Create Event collection structure/type
	- [x] Temporarily use images hosted on the server for upcoming and current events
	- [x] Configure events to have day and timestamps to display events in chronological order, conditionally display current event, and even show how long until the next event occurs.
	- [ ] Format page for different screen size starting with mobile phones!
- [ ] *Home*
	- [x] Format page for different screen size starting with mobile phones!
- [ ] *Navbar*
	- [ ] Format page for different screen size starting with mobile phones!
- [ ] *Middleware*
	- [ ] Ensure protected routes are actually protected





---
# References
