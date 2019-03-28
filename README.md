# Angular Lesson Plan
Note: This lesson plan is for students who have learned React and have had a lesson on typescript. This is actually very similar to what I want to teach my students during regional content week.  This is meant to be a very gentle introduction to Angular.  Obviously this lesson plan will not be going over all concepts but this class could easily be expanded as needed.

In this class we will do a brief overview of Angular with a slide show.  The students will install Angular and make a small project.

## EVERYONE DO: Slideshow (20 minutes)

* [`Angular SlideShow`](https://docs.google.com/presentation/d/1ka0_LxLS1VqEBXbYWrXYqKOXOjrG3g7asKAplDtugJ4/edit?usp=sharing)

In this slideshow, there will be some interactivity for students including pauses for asking questions, a research assignment and installing the Angular framework. The assignments for them include the following:
- Researching 5 Angular Questions on slide 10.  They will have 5 minutes to look up this information.
- Installing Angular. Have students install Angular while the slide is displayed. If you have time, show them the process.  Also slack out this guide for them so they can copy and paste the commands: [Installing Angular](installing-angular.md) This will take 5 minutes. If students are having trouble installing after 5 minutes, have them work with a TA to troubleshoot.  Note: You will have to have these files on your computer to demonstrate Angular in the next section.

## INSTRUCTOR DO (20 minutes)
After you and your students have installed Angular, share your screen and display the src/app folder.  Demonstrate to them the four files for a component: 
- /app.component.html
- /app.component.css
- /app.component.ts
- /app.component.spec.ts (this file is for testing)

Show students what each file looks like.  Don't have them go too deep here, just give them a quick look.

Next, we will create a nav bar for a small site.  Make sure your Angular server is stopped.  Also, g c stands for generate content. Type each line one at a time into your terminal window.

```
> ng generate component nav

> ng g c home

> ng g c about

```
Show students how this has created 3 new folders with component information in each. 

Next, delete the content from app.component.html and place this code in
```
<app-nav></app-nav>

<section>
  <router-outlet></router-outlet>
</section>
```

This code is basically calling the nav component as you can show the students on the browser window "nav works!" - this is the same content from src/app/nav/nav.component.html  Now, replace the code in that file with this:

```
<header>
  <div class="container">
    <nav>
      <ul>
        <li><a routerLink="/">Home</a></li>
        <li><a routerLink="/about">About</a></li>
      </ul>
    </nav>
  </div>
</header>
```
Note: Router link is how we do links in Angular.  A href will not work for this nav.

Show your students the browser again.  They will see two links in a list.

Next, we will add some styles to our project.  Go to nav/component.scss and paste in the following css

```


.container {
  width: 90%;
  margin: 0 auto;
  padding: 1.3em;
  display: grid;
  grid-template-columns: 30% auto;
}
section {
  width: 90%;
  margin: 0 auto;
  padding: 2em;
}

header {
	 background: #666666;
}

 header nav {

   font-family: 'Arial';
   font-size: 18px;
}
 header nav ul {
	 list-style-type: none;
	 margin: 0;
	 padding: 0;
}
 header nav ul li {
	 float: left;
}
 header nav ul li a {
	 padding: 1.5em;
	 text-transform: uppercase;
	 font-size: 0.8em;
   text-decoration: none;
   color:#fff;
}
 header nav ul li a:hover {
	 background: #999;
}

 
```

Lastly, add some routing so that you can switch between the links to display the different components. Open up /src/app/app-routing.module.ts and replace the code with the following:

```
import { NgModule } from '@angular/core';
import { Routes, RouterModule } from '@angular/router';
import { HomeComponent } from './home/home.component';
import { AboutComponent } from './about/about.component';

const routes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'about', component: AboutComponent },
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }

```

Click between the links and show the students how each link works!

## STUDENT DO (10 minutes)
Students will now add their own link to the navigation with a page that they can click to.  Slack out the readme.md and project-starter folder.

## INSTRUCTOR DO (10 minutes)
Review what students had to do
- Run > ng g c linkname in the terminal
- Add a link to this file: src/app/nav/nav.component.html
- Update the routing in /src/app/app-routing.module.ts

Answer any questions, send out the solution, and wrap up!

- This lesson could be extended by adding in templating and adding a form.



