# Custom-Image-Handling
When image is loading from server then show custom image or loader in image section

##add loader image file 
```
assets/images/loader.gif
```

## create new directive file with name image-loader.directive.ts
```
import { Directive, ElementRef, Renderer2, HostListener } from '@angular/core';

@Directive({
	selector: '[imageLoaded]',
})
export class ImageLoadedDirective {
	constructor(private renderer: Renderer2, private element: ElementRef) {
		const parent = this.element.nativeElement;
		this.renderer.addClass(parent, 'placeholder-image');
	}

	@HostListener('error') onError(event) {
		const parent = this.element.nativeElement;
		this.renderer.removeClass(parent, 'placeholder-image');
	}
}

```

## link this directive into your module
```
@NgModule({
	imports: [],
	providers: [
	
	],
	declarations: [ImageLoadedDirective],
	exports: [ImageLoadedDirective],
	entryComponents: [],
})

```

## add this style into your main style sheet
```
.placeholder-image {
	background: url("../assets/images/loader.gif") no-repeat center;
  // set width and height accordingly
}
```

## How to Use?
````
<img [src]="mainImage()" imageLoaded>
````

