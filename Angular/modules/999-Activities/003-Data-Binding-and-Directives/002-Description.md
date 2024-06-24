# Angular Data Binding and Directives 00X: Creating a Tip Calculator

### Contributors:
{ Pablo De La Cruz }

{ Reviewers }

### Prerequisites
1. Basic knowledge of Angular concepts such as components, modules, and templates
2. Familiarity with TypeScript syntax

### Technologies Used
1. Angular
2. TypeScript

# How to Complete
This guided activity will walk through the creation of a simple tip calculator application that utilizes data binding and directives.


### **Step 1:** Create a New Angular Project
Create a new Angular project using the Angular CLI. Press enter for default settings and `cd` into the project. 

```bash
ng new tip-calculator
cd tip-calculator/
```

### **Step 2:** Create a Tip Calculator Component
Create a new component called "tip-calculator" using the Angular CLI.

```bash
ng g component tip-calculator
```

### **Step 3:** Define the Tip Calculator Component Template
Define the template for the tip calculator component. This template should include input fields for the bill amount, the tip percentage, and the number of people, as well as a button for calculating the tip amount per person.

`tip-calculator.component.html`
```html
<!-- 
  In this HTML template, we use Angular's built-in directives to bind data and control the
  display and behavior of the component.

  [(ngModel)] - this directive is used for two-way data binding, binding the state of the input fields to the corresponding component properties and updating them as the input fields are changed

  (click) - this directive is used to listen for a click event on the Calculate Tip button and call the calculateTip method to calculate the tip amount per person

  *ngIf - this structural directive is used to conditionally display the tip amount per person based on whether or not the calculation has been made
-->

<div class="tip-calculator">
    <h2>Tip Calculator</h2>
    <!-- use data binding to bind the billAmount property to the bill amount input field -->
    <label for="billAmount">Bill Amount:</label>
    <input id="billAmount" [(ngModel)]="billAmount" type="number">
    
    <!-- use data binding to bind the tipPercentage property to the tip percentage input field -->
    <label for="tipPercentage">Tip Percentage:</label>
    <input id="tipPercentage" [(ngModel)]="tipPercentage" type="number">
    
    <!-- use data binding to bind the numberOfPeople property to the number of people input field -->
    <label for="numberOfPeople">Number of People:</label>
    <input id="numberOfPeople" [(ngModel)]="numberOfPeople" type="number">
    
    <!-- add a button to calculate the tip amount per person using the click event and calculateTip method -->
    <button (click)="calculateTip()">Calculate Tip</button>
    
    <!-- use *ngIf directive to conditionally display the tip amount per person based on whether or not the calculation has been made -->
    <p *ngIf="tipAmountPerPerson">Tip Amount per Person: {{ tipAmountPerPerson }}</p>
</div>
```

### **Step 4:** Define the Tip Calculator Component Class
Define the class for the tip calculator component. This class should include properties for the bill amount, tip percentage, and number of people, as well as a method for calculating the tip amount per person.

`tip-calculator.component.ts`
```typescript
// We import the Component decorator from Angular core library which is used to define a new component
import { Component } from '@angular/core';

// Component decorator is used to decorate the class and specify metadata about the component
@Component({
  // Selector is a CSS selector for an HTML element that represents the component
  selector: 'app-tip-calculator',
  // Template URL is the path to an external file that contains the component's template
  templateUrl: './tip-calculator.component.html',
  // Style URLs is an array of paths to external CSS files that contain styles for the component
  styleUrls: ['./tip-calculator.component.css']
})
// We define a new class and export it so that it can be used in other parts of the application by default
export class TipCalculatorComponent {
  // We define class properties and initialize them with default values of 0
  billAmount: number = 0;
  tipPercentage: number = 0;
  numberOfPeople: number = 0;
  tipAmountPerPerson: number = 0;

  // We define a method that calculates the tip amount per person based on user inputs
  calculateTip() {
    // We calculate the tip amount using the bill amount and tip percentage inputs
    const tipAmount = (this.billAmount * this.tipPercentage) / 100;
    // We calculate the tip amount per person by dividing the tip amount by the number of people input
    this.tipAmountPerPerson = tipAmount / this.numberOfPeople;
  }
}
```

### **Step 5:** Style and save time by pasting tip-calculator.component.ts code.
`tip-calculator.component.css`
```css
.tip-calculator {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f8f8f8;
  }
  
  h2 {
    font-size: 24px;
    font-weight: bold;
    margin-bottom: 20px;
  }
  
  label {
    display: inline-block;
    font-size: 18px;
    font-weight: bold;
    margin-bottom: 10px;
  }
  
  input[type="number"] {
    width: 100%;
    padding: 10px;
    font-size: 16px;
    border: 1px solid #ccc;
    border-radius: 3px;
    box-sizing: border-box;
  }
  
  button {
    display: block;
    margin: 20px 0;
    padding: 10px 20px;
    font-size: 18px;
    font-weight: bold;
    text-transform: uppercase;
    color: #fff;
    background-color: #337ab7;
    border: none;
    border-radius: 3px;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #286090;
  }
  
  p {
    font-size: 18px;
    margin-top: 20px;
  }
```

### **Step 6:** The App Component
Replace the default app component template with the tip calculator component.

`app.component.html`
```html
<div>
  <app-tip-calculator></app-tip-calculator>
</div>
```

Add and import `FormsModule` to app.module.ts

`app.module.ts`
```typescript
  imports: [
    BrowserModule,
    FormsModule
  ],
```

### **Step 7:** Run and test the Application
Run the application using the Angular CLI. The `--open` option automatically opens your browser to http://localhost:4200/.

```bash
ng serve --open
```



# Cumulative for the  Data Binding and Directives
