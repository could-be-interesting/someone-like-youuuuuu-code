## Mistakes and the silverlining for those mistakes.

## Mistake no. 1, overriding  MaterialUI classNames to work by nesting SCSS.
What led to the trouble: 
1) The initial material UI theme colors did not match the final colors application.
2) Sometimes buttons needed width's most of this could be solved with width '100%'.

#### Overriding materialUI being required:
MaterialUI documentation mentions `import { withStyles } from '@material-ui/core/styles';`
<br/>run the withStyles(classes) function for each component that needs an override.
1) in the beginning we were putting these on the very large class.
2) A more correct is to have a single file named CustomMaterialUI that brings that implements 
the different materialUI components in a custom fashion and importing those components into your application. 
Example: `<ButtonPadding10/>` ... the class still requires withStyles(classes)

3) Overriding is possible with inline styles, but due to some pushback this method was rejected.
4) A css hack was discovered where using nested scss; the postprocessor will add the className after materialUI 
has evaluated styling. This allowed overriding materialUI classes using normal css classes.

## Mistake no. 2, 
nesting the entire tachyons library into an scss file:
<br/>example: 
```
/* scss */
.tachyons {
  .entire_tachions_library
}
```

The real nail in the coffin, 
```
/* src/index.js */
import './tachyons.scss';
ReactDOM.render(<App className="tachyons"/>, document.getElementById('root'));
```

Not sure the specific hit to performance for this action. But overall these many decisions are a performance hog.
1) MaterialUI is a large library.
2) SCSS is translating a nested tachyons library.
3) tachyons is not overly large 117 kb, and gzipped 17.7 kb.

The application is functional not a noticable performance hit adding a nested tachyons metrics for the actions still needs to be completed.

## Silver lining:
The entire application can simplify css using tachyons, 
<br/>This allows the use of a single css file and making the most out of shared classes.

Also a globalNestedScss.scss file is used to catch the edge cases that tachyons is not handling.
<br/>example: tachyons uses 0.25rem which equates to roughly 4px.
<br/>But in padding needs to be 10px on a materialUI button our globalcssfile can have:
```
.globalCSS {
  .pd-px-10
}
```

... but its still slow right? (pending official researching performance metrics)
<br/>Here are some positives: 
<br/>Easy to revert after the fact, if nesting tachyons is bad tachyons can be shifted 
to use css and the materialUI overrides can be shifted to the CustomMaterialUI file.

alternatively: 
```
.globalCSS {
  .pd-px-10
}
```
Care must be taken with globalCSS file to have seperate names from css classes. 
However, a unique key such as "gl" can be prefixed to all global styles: `.gl_pd-px-10 `
