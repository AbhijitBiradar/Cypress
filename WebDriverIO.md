

WebDriverIO Code Snippet

await browser.get("URL Details");
await browser.getTitle();
await expect(browser).toHaveTitleContaining("expected title");
await expect($("p")).toHaveTextContaining("userName is Abhijit");
await browser.pause(3000);

for more assertion, refer this
https://webdriver.io/docs/api/expect-webdriverio/


locator Methods
await $("#userName").setValue("Abhijit");
await $("#login").click();
await $(".alertText").getText();

await browser.waitUntil(async ()=> await $("#signInBtn").getAttribute('value')==='Sign In',
{
	timeout:5000,
	timeoutMsg: ' Error message is not showing up'
})

for more on waitUntil, refer this
https://webdriver.io/docs/api/element/waitUntil/

await $(".btn-primary").waitForExist();
await expect(browser).toHaveUrlContaining("shop");
await expect(browser).toHaveTitle("ProtoCommerce");


use below url, to configure execution for other browser
https://webdriver.io/docs/selenium-standalone-service

way 1:
cosnt radioButtons= await $$(".customradio");
const userDropDown=radioButtons[1];
await userDropDown.$("span").click();

way 2:
await $$(".customradio")[0].$("span").click();


cosnt modal=$(".modal-body");
await modal.waitForDisplayed();

await $$(".customradio")[0].$("span").isSelected();

await expect(modal).not.toBeDisplayed();

//code for dropdown
const dropdown =await $("select form-control");
await dropdown.selectByAttribute('value','teach');
await dropdown.selectByVisibleText("consultant");
await dropdown.selectByIndex(0);
console.log(await dropdown.getValue());


//use chai library for assertion
step 1: import library
const expectChai=require('chai').expect;

step 2: Execute code
expectChai(await dropdown.getValue()).to.equal("stud");

//display  item from dropdown
let items = await $$("[class ='ui-menu-item'] div");
for(var i=0;i< await items.length;i++){
	console.log(await items[i].getText());
	if(await items[i].getText()==="India"){
		await items[i].click();
		break;
	}
}

//code for checkbox
cosnt element=await $$("input[type='checkbox']");
await element[1].click();
console.log(await element[1].isSelected());
console.log(await element[2].isSelected());

//code to capture screenshot
await browser.saveScreenshot("file1.png");


//code for scrolling
await $("#dpdid").scrollIntoView();
await $("#dpdid").moveTo();


JavaScript Alerts
await browser.isAlertOpen();
expectChai(await browser.isAlertOpen()).to.be.true;
expect(await browser.getAlertText()).to.equal("Sample alert text");
await browser.acceptAlert();

//compare two arrays
const foodList=await $$("tr td:nth-child(1)").map(async veggie=> await veggie.getText());
const sortedFood=foodList.sort();
expectChai(foodList).to.eql(sortedFood);

install vs code javascrpt webdriverio debugger
https://webdriver.io/docs/debugging/
https://marketplace.visualstudio.com/items?itemName=ms-vscode.js-debug-nightly

//create a copy of arrays
veggies=originalVeggiesnames.slice();

const(arrayfoods).toBeElementsArrayOfSize({eq:5});

//code to get window handles
const handles= await browser.getWindowHandles();
await browser.switchToWindow(handles[1]);
await browser.closeWindow();

//code to open new window
await browser.newWindow("https://www.google.com");

//switch to existing tab or window
await browser.switchWindow("https://exsitngwindow.com");

//code to get Hyperlink count on page
$$("a").length

//code to switch to frame
browser.switchToFrame($("[id='course-frame']"));

//wait for not exist
await $(".elipsis").waitForExist("reverse:true});

//Read test data from JSON file 
const fs=require('fs');
let testData=JSON.parse(fs.readFileSync('JSON\FILE\PATH'));

testData.forEach(({userName,password})=>{

});


//execute specific suite 
npx wdio run wdio.conf.js --mochaOpts.grep Smoke

note: mention smoke in description of it block


//execute test suite with specif files

File : wdio.conf.js

suites:{
	<TestSuiteName>: [<TestFileName1/with/Path>,
			<TestFileName2/with/Path>
	]
}

npx wdio run wdio.conf.js --suite <TestSuiteName>

//command to provide test file runtime from command prompt
npx wdio run wdio.conf.js --spec <Spec\file]\path>


//command to exclude spec file from execution

File : wdio.conf.js

exclude: [
	<TestFileName1/with/Path>,
	<TestFileName2/with/Path>
]

//code to retry test again
this.retries(3);


//command to start jenkins
java -jar jenkins.war -httpPort=<AvailablePort>































