# apnacollege-demo
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  standalone: true,
  name: 'age'
})
export class AgePipe implements PipeTransform {
  transform(value: number): string {
    if (value === 1) {
      return '1 year';
    } else {
      return ${value} years;
    }
  }
}


import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  standalone: true,
  name: 'ratings'
})
export class RatingPipe implements PipeTransform {
  transform(rating: number): string {
    // Ensure rating is within 0 to 5
    const fullStars = Math.floor(rating);  // full stars (whole number)
    const hasHalfStar = rating % 1 >= 0.5; // check if there's a half star
    const emptyStars = 5 - fullStars - (hasHalfStar ? 1 : 0); // remaining empty stars

    // Construct the star string based on full, half, and empty stars
    return '★'.repeat(fullStars) + (hasHalfStar ? '☆' : '') + '☆'.repeat(emptyStars);
  }
} 


import {Directive, ElementRef, HostListener, Input} from '@angular/core';

@Directive({
  standalone: true,
  selector: '[appHoverDirective]'
})
export class HoverDirectiveDirective {
  @Input() appHoverHighlight = '';
  constructor(private el: ElementRef) {}

  @HostListener('mouseenter') onMouseEnter() {
    this.highlight(this.appHoverHighlight || 'yellow');
  }
  @HostListener('mouseleave') onMouseLeave() {
    this.highlight('');
  }
  private highlight(color: string) {
    this.el.nativeElement.style.backgroundColor = color;
  }
}
