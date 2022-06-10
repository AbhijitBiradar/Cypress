Cypress Code Snippet

1. Insstall nodejs
2. Configure path for nodeJS. Refer below video
	https://www.udemy.com/course/cypress-tutorial/learn/lecture/26426106#announcements
3. Create package.json using below steps
	a. create project folder
	2. fire command on terminal npm -i init
4. command npm install cypress --save-dev
5. Enter command node_module\.bin\cypress open


cy.visit("http://www.google.com");

In the upcoming lectures we shall use below demo website for demonstration of few Cypress topics

https://rahulshettyacademy.com/seleniumPractise/#/

cypress supports only CSS selector locator

cy.get('.search-keyword').type('ca');

cy.wait(3000);

//code to check elemets which are visible only
cy.get('.search-keyword:visible')

//search for second elemet
cy.get('.products').find('.product).eq(2);

//parent child chaining
cy.get('.products').find('.product).should('have.length', 4);

cy.get('.products').find('.product).eq(2).contains('ADD TO CART').click();

//code to iterate through multiple elements
cy.get('.products).find(.product).each($e1, index, $list)=>{
	const texveg=$e1.find('h4.product-name').text();
	if(texveg.includes('cashews'){
		cy.wrap($e1).find('button').click();
	}
}

cy.get('.brand').should('have.text',GREENKART');

//handling promises in cypress
cy.get('.brand').then(function(logoElement){
	cy.log(logoElement.text());
});

//alias locator
cy.get('.products).as('productLocator);
cy.get(@productLocator).find('.product').should('have.length',4);

cy.get('@productLocator').find('.product').eq(2).contains('ADD TO CART').click().then(function(){
    console.log('sf')
})

cy.get('.cart-icon > img').click()

//for checkbox
cy.get('#checkbox1').check().should('be.checked').and('have.value','option1');

//uncheck
cy.get('#checkbox1').uncheck().should('not.be.checked');

//checck multiple checkbox
cy.get('input[type="checckbox"]').check(['option2',''option3']);

//static dropdown
cy.get('select').select('option1');
//assertion
//cy.get('select').should('have.value','option2');


//dynamic dropdown
cy.get('autocomplete').should('have.value','India');


//visibility
cy.get('#textbox1').should('be.visible);
cy.get('#hidebutton').click();
cy.get('#textbox1').should('not.be.visible);

//radio button
cy.get('#radio2').check();
cy.get('#radio2').should(be.checked');

//popup
cy.get(#alertbtn).click();
cy.get('[value=confirm]').click();

//validate text of alertbtn
cy.on('window:alert', (str)=>{
	expect(str).to.equal('Hello, share this practise page')
});

cy.on('window:confirm', (str)=>{
	expect(str).to.equal('Hello, are you sure you want to confirm')
});

//invoke new tab
//cypress doesn't support new tab. It opens the page in the same tab
cy.get('#opentab').invoke('removeAttr','target).click()    //refer jquery for this

//navigate back
cy.go('back');

//verify the url
cy.url().should('include','qaclickacademy');

going through static table
cy.get('tr td:nth-child(2)').each(($e1, index, $list) => {
 
    const text=$e1.text()
    if(text.includes("Python"))
    {
 
        cy.get("tr td:nth-child(2)").eq(index).next().then(function(price)
        {
         const priceText=   price.text()
         expect(priceText).to.equal('26')
        })
    }
 
})

//mouse hover events are not supported in cypress. Below is work-arround using jquery
cy.get('div.mouse-hover-content').invoke('show');

//Handle invisible element
cy.contains('top').click({force:true});
