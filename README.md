# Angular-InterView



## 1 - What is Angular Framework?
Angular is a TypeScript-based open-source front-end platform

## 2 - What is the difference between AngularJS and Angular?
- AngularJS	
It is based on MVC architecture	
It uses JavaScript to build the application	
Based on controllers concept	
Not a mobile friendly framework	
Difficulty in SEO friendly application development	

- Angular
This is based on Service/Controller
Introduced the TypeScript to write the application
This is a component based UI approach
Developed considering mobile platform
Ease to create SEO friendly applications

## 3 - What is TypeScript?
TypeScript is a typed superset of JavaScript

## 5 - What are the key components of Angular?
> Component
> Modules
> Templates
> Services
> Metadata

## 6 - What are directives?
Directives add behaviour to an existing DOM element

## 7 - What are components?
Components are the most basic UI building block 

## 8 - What are the differences between Component and Directive?
- Component
@Component meta-data annotation
used to create UI widgets
break up the application into smaller components
Only one component can be present per DOM element
@View decorator or templateurl/template are mandatory

- Directive
@Directive
add behavior to an existing DOM element
design re-usable components
Many directives can be used per DOM element
Directive doesn't use View

## 9 - What is a template?
A template is a HTML view

## 10 - What is a module?
Modules are logical boundaries in application and the application is divided into separate modules to separate the functionality of application.
```sh
@NgModule ({
   imports:      [ BrowserModule ],
   declarations (Declare the class types ): [ AppComponent, YourPipe, YourDirective ], 
-classes shouldn't be declared-: (A class that's already declared in another NgModule/ Ngmodule/ Service/ Helper classes)
   bootstrap:    [ AppComponent ],
   providers: []
})
export class AppModule { }
```
## 11 - What are lifecycle hooks available?
Angular application goes through an entire set of processes or has a lifecycle right from its initiation to the end of the application.
- Constructor: A default method which is called when the class is instantiated.
- ngOnChanges: Executes when a new component is created
- ngOnInit: This is called whenever the initialization of the directive/component
- ngDoCheck: Runs when change detection runs.
- ngAfterContentInit: This is called after content(ng-content) has been projected into the view.
- ngAfterContentChecked: This is called after every projected content has been checked
- ngAfterViewInit: Called after the components view (and child view) has been initialized.
- ngAfterViewChecked: Called every time the view (and child view) has been checked.
- ngOnDestroy: This is the cleanup phase just before Angular destroys the directive/component.

12 - What is a data binding?
allows to define communication between a component and the DOM
- From the Component to the DOM:
Interpolation: {{ value }}: Adds the value of a property from the component
Property binding: [property]=”value”: The value is passed from the component to the specified property or simple HTML attribute

- From the DOM to the Component:
Event binding: (event)=”function”

- Two-way binding: Two-way data binding:
[(ngModel)]=”value”: Two-way data binding allows to have the data flow both ways

13 - What is metadata?
Metadata is used to decorate a class/Property/Method/Parameter so that it can configure the expected behavior

- class: @Component and @NgModule @Directive() @Pipe() @Injectable()
- Property / class field : @Input() @Output() myEvent = new EventEmitter();
- Method: @HostListener('click', ['$event'])
    onHostClick(event: Event) {
        // clicked, `event` available
    }
- Parameter: constructor(@Inject(MyService) myService)

16 - What is a service?
A service is used when a common functionality needs to be provided to various modules

17 - What is dependency injection in Angular?
is an important application design pattern in which a class asks for dependencies from external sources rather than creating them itself.

19 - What is the purpose of async pipe?
The AsyncPipe subscribes to an observable or promise and returns the latest value it has emitted

21 - What is the purpose of ngFor directive?
We use in the template to display each item in the list.

22 - What is the purpose of ngIf directive?
inserts or removes an element based on a truthy/falsy condition

25 - What are template expressions?
[property]="expression" / {{username}}
- expressions are prohibited in template expression
assignments (=, +=, -=, ...)
new
chaining expressions with ; or ,
increment and decrement operators (++ and --)

26 - What are template statements?
The template statements appear in quotes to the right of the = symbol like (event)="statement".
Also there are statements not allowed

28 - What are pipes?
takes in data as input and transforms it to a desired output

32 - Give an example of custom pipe?
@Pipe({name: 'customFileSizePipe'})
  export class FileSizePipe implements PipeTransform {
    transform(size: number, extension: string = 'MB'): string {
      return (size / (1024 * 1024)).toFixed(2) + extension;
    }
  }

33 - What is the difference between pure and impure pipe?
- pure pipe: is only called when Angular detects a change in the value or the parameters passed to a pipe
- An impure pipe: is called for every change detection cycle no matter whether the value or parameters changes.

36 - What is HttpClient and its benefits?
- a simplified client HTTP API which is based on top of XMLHttpRequest interface
Contains testability features
Provides typed request and response objects
Intercept request and response
Supports Observalbe APIs
Supports streamlined error handling

38 - How can you read full response?
(this.userUrl, { observe: 'response' });

39 - How do you perform Error handling?
by passing error object as a second callback to subscribe() method.

45 - What is multicasting?
is the practice of broadcasting to a list of multiple subscribers in a single execution.

46 - What are observable creation functions?
- from a promise
- from an AJAX request
- from a counter
- from an event

60 - What are the various kinds of directives?
- Components: directives with a template
- Structural directives: change the DOM layout by adding and removing DOM elements.
- Attribute directives: change the appearance or behavior of an element
@Directive({
  selector: '[appHighlight]'
})
export class HighlightDirective {
    constructor(el: ElementRef) {
       el.nativeElement.style.backgroundColor = 'red';
    }
}
<p appHighlight>Highlight me!</p>

66 - What is router outlet?
is a directive from the router library and it acts as a placeholder that marks the spot in the template where the router should display
- ActivatedRoute contains the information about a route associated with a component loaded in an outlet

67 - What are router links?
is a directive on the anchor tags give the router control over those elements.
- RouterLinkActive is a directive that toggles css classes for active RouterLink bindings based on the current RouterState
- RouterState is a tree of activated routes
- configures the router with routes via the RouterModule.forRoot(routesArrayName)

70 - What are router events?
During each navigation, the Router emits navigation events through the Router.events property allowing you to track the lifecycle of the route.
- NavigationStart
- ....
- GuardsCheckStart
- .....
- NavigationEnd
- NavigationCancel
- NavigationError
- Scroll

129 - What is a DI token?
A DI token is a lookup token associated with a dependency provider in dependency injection system

130 - What is Angular DSL?
A domain-specific language (DSL) like (), [], *

136 - What is platform in Angular?
A platform is the context in which an Angular application runs.
- While running in the browser, it uses platform-browser package.
- When SSR(server-side rendering ) is used, it uses platform-server

138 - How do you select an element with in a component template?
<input #uname>

@ViewChild('uname') input;

ngAfterViewInit() {
  console.log(this.input.nativeElement.value);
}

139 - How do you detect route change in Angular?
this.router.events.subscribe((event: Event) => {
            if (event instanceof NavigationStart) {
                // Show loading indicator and perform an action
            }
}

140 - How do you pass headers for HTTP client?
- first :
this._http.get('someUrl',{
   headers: {'header1':'value1','header2':'value2'}
});

Or:
let headers = new HttpHeaders().set('header1', headerValue1); // create header object
headers = headers.append('header2', headerValue2); // add a new header

let params = new HttpParams().set('param1', value1); // create params object
params = params.append('param2', value2); // add a new param,

return this._http.get<any[]>('someUrl', { headers: headers, params: params })

142 - Is Angular supports dynamic imports?
- Yes, You can use the import statement for lazy loading the module using loadChildren
{path: ‘user’, loadChildren: () => import(‘./users/user.module’).then(m => m.UserModule)};

143 - What is lazy loading?
Lazy loading is one of the most useful concepts of Angular Routing. It helps us to download the web pages in chunks instead of downloading everything in a big bundle. It is used for lazy loading by asynchronously loading the feature module for routing whenever required using the property loadChildren

0 - Polyfills make your application compatible for different browsers.

151 - What are the ways to trigger change detection in Angular?
- ApplicationRef.tick(): Invoke this method to explicitly process change detection and its side-effects. It check the full component tree.
- NgZone.run(callback): It evaluate the callback function inside the Angular zone.
- ChangeDetectorRef.detectChanges(): It detects only the components and it's children.

153 - What are the security principles in angular?
- You should avoid direct use of the DOM APIs.
- You should enable Content Security Policy (CSP) and configure your web server to return appropriate CSP HTTP headers.
- You should Use the offline template compiler.
- You should Use Server Side XSS protection.
- You should Use DOM Sanitizer.
- You should Preventing CSRF or XSRF attacks.

165 - What is Sanitization? Is angular supports it?
Sanitization is the inspection of an untrusted value, turning it into a value that's safe to insert into the DOM. Yes,

170 - What is DOM sanitizer?
DomSanitizer is used to help preventing Cross Site Scripting Security bugs (XSS)

173 - What are Http Interceptors?
It is an interface that can perform a variety of implicit tasks on HTTP requests/ responses, from authentication to logging.
interface HttpInterceptor {
  intercept(req: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>>
}
@Injectable()
export class MyInterceptor implements HttpInterceptor {
    constructor() {}
    intercept(req: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {
        ...
    }
}
@NgModule({
    ...
    providers: [
        {
            provide: HTTP_INTERCEPTORS,
            useClass: MyInterceptor,
            multi: true
        }
    ]
    ...
})

190 - What is AOT compiler?
It converts your Angular HTML and TypeScript code into efficient JavaScript code during the build phase before the browser downloads and runs that code.

191 - How do you select an element in component template?
By injecting ElementRef
constructor(myElement: ElementRef) {
   el.nativeElement.style.backgroundColor = 'yellow';
}

198 - What is router state?
The RouteState is an interface which represents the state of the router as a tree of activated routes.

-- The trackBy function determines when a div element created by the ngFor loop should be re-rendered (replaced by a new element in the DOM)

207 - What is safe navigation operator?
- ?
{{user?.fullName.firstName}}

208 - Is any special configuration required for Angular9?
In tsconfig.json
"angularCompilerOptions": {    "enableIvy": true  }

210 - Is mandatory to pass static flag for ViewChild?
@ViewChild(ChildDirective) child: ChildDirective; // Angular9 usage
@ViewChild(ChildDirective, { static: false }) child: ChildDirective; //Angular8 usage

--- load modules in the background :
import { NgModule } from '@angular/core';
import {Routes, RouterModule, PreloadAllModules} from '@angular/router';
const routes: Routes = [
  { path: 'about', loadChildren: () => import('./about/about.module').then(m => m.AboutModule) },
  { path: 'users', loadChildren: () => import('./users/users.module').then(m => m.UsersModule)},
  { path: '', redirectTo: '', pathMatch: 'full'}
  ];
@NgModule({
  imports: [RouterModule.forRoot(routes, {
    preloadingStrategy: PreloadAllModules
  })],
  exports: [RouterModule]
})
export class AppRoutingModule { }

256 - What are reactive forms?
Reactive forms is a model-driven approach for creating forms in a reactive style
These are built around observable streams, where form inputs and values are provided as streams of input values

- also there is dynamic forms

258 - What are template driven forms?
Template driven forms are model-driven forms where you write the logic, validations, controls etc, in the template part of the code using directives.

259 - What are the differences between reactive forms and template driven forms?

Feature	                                 Reactive	                                        Template-Driven
Form model setup	Created(FormControl instance) in component explicitly	               Created by directives
Data updates	             Synchronous	                                                Asynchronous
Form custom validation	   Defined as Functions	                                               Defined as Directives
Mutability	        Immutable(by always returning new value for FormControl instance)	       Mutable(Property always modified to new value)
Scalability	          More scalable using low-level APIs	                                      Less scalable using due to abstraction on APIs

260 - What are the different ways to group form controls?
- FormGroup: It defines a form with a fixed set of controls those can be managed together in an one object.
- FormArray: It defines a dynamic form in an array format, where you can add and remove controls at run time.

261 - How do you update specific properties of a form model?
patchValue()
setValue

262 - What is the purpose of FormBuilder?
is used as syntactic sugar for easily creating instances of a FormControl, FormGroup, or FormArray. This is helpful to reduce the amount of boilerplate needed to build complex reactive forms

263 - How do you verify the model changes in forms?
- by adding a getter property

model = new User('John', 29, 'Writer');
get diagnostic() { return JSON.stringify(this.model); }

{{diagnostic}}

266 - What are the types of validator functions?
- Sync validators: which take a control instance and immediately return either a set of validation errors or null.
- Async validators: which take a control instance and return a Promise or Observable that later emits a set of validation errors or null

268 - How do you optimize the performance of async validators?

- <input [(ngModel)]="name" [ngModelOptions]="{updateOn: 'blur'}">
- name = new FormControl('', {updateOn: 'blur'});

270 - What is host property in css?
:host pseudo-class selector is used to target styles in the element that hosts the component

--- routing things:
-- from route: ActivatedRoute
- Param:
this.route.paramMap.pipe(
    switchMap(params => {
      this.selectedId = Number(params.get('id'));
      return this.service.getHeroes();
    })
  );

Or this.route.snapshot.paramMap.get('id');

- query params:
this.route.queryParams.subscribe(params => { .. });

-- from router: Router
- navigate:
this.router.navigate(['items'], { relativeTo: this.route })
- get the current route
this.router.url

--- ViewEncapsulation
- ViewEncapsulation.None:
There is no shadow DOM.
Style is not scoped to the component.

- ViewEncapsulation.Native:
Angular creates a Shadow DOM (#shadow-root) and the style is scoped to that Shadow DOM.

-ViewEncapsulation.Emulated:
Angular will not create a Shadow DOM(but it will generate like id h1[_ngcontent-c0]) for the component.
Style will be scoped to the component.
This is the default value for encapsulation.

111 - What is Angular Ivy?
Ivy is a new rendering engine for Angular

112 - What are the features included in ivy preview?
Generated code that is easier to read and debug at runtime
Faster re-build time
Improved payload size
Improved template type checking
