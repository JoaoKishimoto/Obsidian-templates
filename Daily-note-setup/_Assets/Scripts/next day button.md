---
created: 09-07-2025
modified: 13-05-2026
---
<%*
const currentFileName = await tp.file.title; // gets the daily note
const template = await tp.file.find_tfile('_Assets/Templates/Daily');
const currentDate = moment(currentFileName, "YYYY-MM-DD ddd");
const nextDate = currentDate.clone().add(1, 'days');
const paste = nextDate.format('YYYY-MMMM');
const fullDate = nextDate.format('YYYY-MM-DD ddd');
const fullFilePath = `Routine/${paste}/${fullDate}`;
const filePath = `Routine/${paste}/`;
const weekDay = nextDate.format("ddd");

createIfNeeded(fullFilePath, filePath, fullDate);
setTimeout(addRoutine, 500, fullFilePath, weekDay);

async function createIfNeeded(fullFilePath, filePath, fullDate) {	
	// creates or opens the file
	if(tp.file.exists(fullFilePath)) {
		await app.workspace.openLinkText(fullFilePath, "", true);
	} else {
		await tp.file.create_new(template, fullDate, true, filePath)
	}
}

async function addRoutine(fullFilePath, weekDay){
	let file = app.vault.getAbstractFileByPath(`${fullFilePath}.md`);
	let data = "";
	
	if(weekDay == "Mon"){
		data = `- [ ] add monday routine here	`;
	}
	// you can utilize the || symbol to OR, if 2 or more days have the same routine
	// like the following:
	// else if(weekDay == "Tue" || weekDay == "Thu"){
	else if(weekDay == "Tue"){
		data = `- [ ] exemple task 1
- [ ] example task 2 \n`;
	}

	else if (weekDay == "Wed") {
		data = `- [ ] exemple task 1
- [ ] example task 2 \n`;
	}

	else if(weekDay == "Thu"){
		data = `- [ ] exemple task 1
- [ ] example task 2 \n`;
	}

	else if(weekDay == "Fri"){
			data = `- [ ] exemple task 1
- [ ] example task 2 \n`;
	}
	
	await app.vault.append(file, data);
}
%>