// Your recommended changes go here

# Ad Hoc Homework: Accessibility

## List of some recommendations for improvements to the provider search section in healthcare.gov/see-plans/


### Technical changes: HTML, CSS, Javascript, ARIA attributes

1. Focus goes to an element that is not visible and is announced as “Not Covered” in Search Results
Using macOS VoiceOver+Safari, on the “View health & dental plans” page where search results are listed, after navigating to “Medical Providers In-network”, focus then goes to an element that is not visible and is announced as “Not Covered”. “Medical Providers In-network” is first focused and announced, then an element that is not visible is focused and is announced as “Not Covered”, then focus moves to the doctor’s name (ex., dr. Kimberly Y Smith M.d.).

 The element that is not visible should not be focused or announced as “Not Covered”, since it would cause confusion for the screen reader user. This section lists “Medical Providers In-network” and when it announces “Not Covered”, it is conflicting information provided for the user. This can be especially confusing if users are not able to see the screen while the focus is on an empty element.

<!-- HTML:
<li class="pet-c-status-list__item ds-u-font-size--small pet-u-overflow-wrap--break-word pet-c-status-list__item--no"><span 
class="ds-u-visibility--screen-reader">Not Covered</span><span class="ds-u-text-transform--capitalize">dr. kimberly y smith  
m.d.</span> </li> -->

Note that this issue also occurs in the “Plan features” and “Drugs covered/Not covered” sections to the right and left of this section (“Medical Providers In-network”).

This is a Focus Order issue that is not in compliance with WCAG 2.4.3.

The span that contains “Not Covered” can be removed (unless it is there to serve another purpose, in which case, it can be hidden using aria-hidden=”true”) so that it is not focused nor announced and screen reader users will not receive this conflicting information.

2. Checkboxes allow users to check two options when the result only considers one of the options
On the “See if your doctors, facilities & drugs are covered” page, when both checkboxes (“Doctors & facilities” and “Prescription drugs”) are simultaneously checked, after clicking “Continue” the user is brought to the “Add your doctors & facilities” page. This could be confusing since the user also checked the box to search for “Prescription drugs”, and would expect to be able to search for both “Doctors & facilities” and “Prescription drugs”, but are only given the option to search for “Doctors & facilities”.

<!-- HTML:
<fieldset class="ds-c-fieldset"><legend class="ds-c-label"><span class="">What do you want to search for?</span></legend><div><input \class="ds-c-choice" id="checkbox_pages_203" name="pages" type="checkbox" value="visitProviders"><label class="ds-c-label" \for="checkbox_pages_203"><span class="">Doctors &amp; facilities</span></label></div><div><input class="ds-c-choice" id="checkbox_pages_204" name="pages" type="checkbox" value="visitDrugs"><label class="ds-c-label" for="checkbox_pages_204"><span class="">Prescription drugs</span></label></div></fieldset> -->

Instead of using checkboxes here, use radio buttons. With radio buttons, only one option can be selected at a time. So, if the user would like to search for “Doctors & facilities”, they can select the radio button next to that option. And if the user would like to search for “Prescription drugs”, they can select the radio button next to that option. Doing so will unselect the radio button next to “Doctors & facilities” if it was selected, and vice versa. For more information on choosing to use checkboxes vs. radio buttons, please see: https://www.justinmind.com/blog/checkboxes-or-radio-buttons-let-the-ui-design-battle-commence/

Since this is an issue where the role of the element needs to be changed, it is related to the compliance of WCAG 4.1.2.

### Content
1. Link text “View steps” needs to be more descriptive of where the link leads to.
The link text “View steps” at the top of the “Add your doctors & facilities” page (and also other pages) may be confusing to the user.  It may be unclear which steps they can view by clicking the link--steps to see if doctors, facilities, & drugs are covered, or the general steps overview? Perhaps using link text that is more descriptive and specific, such as “View steps overview”, would be helpful to the user to make this distinction.

<!-- HTML:
<a class="ds-u-margin-left--2" href="#/steps">View steps</a> -->

The link text needs to be sufficiently descriptive of the link’s purpose so that it can be in compliance with WCAG 2.4.4.





