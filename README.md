# WebsiteContent

Content for the public website

# Template Files

Content resides in template files that are commonly named `<some_name>.html.ep`. 
In these files, common HTML tags and BS4 classes can be used, as well as 
special Mojolicious helpers and Perl code injection. However, the latter 
should be reserved for administrators.

# TODO

Implement functionality to disable Google Analytics, done ideally together 
with accepting cookies. The snippet to set is:

```window['ga-disable-UA-167172139-1'] = true;```

That is required on every page.

```{html}
<a href="javascript:gaOptout()">Click here to opt-out of Google Analytics</a>

<script>
// Set to the same value as the web property used on the site
var gaProperty = 'UA-167172139-1';

// Disable tracking if the opt-out cookie exists.
var disableStr = 'ga-disable-' + gaProperty;
if (document.cookie.indexOf(disableStr + '=true') > -1) {
  window[disableStr] = true;
}

// Opt-out function
function gaOptout() {
  document.cookie = disableStr + '=true; expires=Thu, 31 Dec 2099 23:59:59 UTC; path=/';
  window[disableStr] = true;
}
</script>


```

The script can go into the custom scripts, but the check must be done in the 
header of the main layout, which be used to feed every single page.
