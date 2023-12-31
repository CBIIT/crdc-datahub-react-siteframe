# NCI branded Webpage Base (React)

This is a base layout of an NCI branded webpage with configurable header and footer components.

## Header Configuration
To replace the NCI logo with another logo: 
- Replace src/assets/header/Portal_Logo.svg with the desktop version
- Replace src/assets/header/Portal_Logo_Small.svg with the tablet/mobile version of the logo you want to use.\
Why

To change the desktop navigation bar 
- Head to src/config/globalHeaderData.tsx
- To add an item to the navbar, add an element to navMobileList
1. Name is what will appear on the navbar
2. If className is set to 'navMobileItem', this is a link element, and clicking on this navbar element will navigate the page to the link set in the link field.
3. If className is set to 'navMobileItem clickable', this is a dropdown. Cicking on this navbar element will expand a dropdown to display elements set in navbarSublists. The link field for element is ignored.
4. Please set the id field to the ID this element should have for QA purposes.\
Examples:
~~~~
{
    name: 'Home',
    link: '',
    id: 'navbar-link-home',
    className: 'navMobileItem'
}
~~~~
This navbar element titled home links to home, with an id of navbar-link-home.
~~~~
  {
    name: 'About',
    link: '',
    id: 'navbar-dropdown-about',
    className: 'navMobileItem clickable',
  }
~~~~
This navbar element titled about will be a dropdown, with an id of navbar-dropdown-about.
~~~~
  {
    name: 'Other Navbar Item',
    link: '',
    id: 'navbar-dropdown-test-other-navbar-item',
    className: 'navMobileItem clickable',
  },
~~~~
This navbar element titled Other Navbar Item is a dropdown. The ID styling is shown as well.

- To configure the dropdowns inside the navbar. Add a new mapping to navbarSublists
1. Sublists only contain links.
2. Name is what will appear on the navbar
3. Text is optional, and appears below the name
4. ID has the format 'navbar-dropdown-item-{name}'
5. Link is what clicking on the sublist link will navigate to
6. Classname is either navMobileSubItem or navMobileSubTitle, this will be explained later when configuring the tablet/mobile menu. \
Examples:
~~~~
  export const navbarSublists = {
  "Other Navbar Item": [
    {
      name: 'Navbar subitem # 1',
      link: '/subitemlink1',
      text: 'testText for subitem #1',
      id: 'navbar-dropdown-item-navbar-subitem-1',
      className: 'navMobileSubItem',
    },
    {
      name: 'Navbar subitem #2',
      link: '/subitemlink2',
      id: 'navbar-dropdown-item-navbar-subitem-2',
      className: 'navMobileSubItem',
    },
],
  About: [
    {
      name: 'Other Resources',
      link: '/or',
      id: 'navbar-dropdown-item-other-resources',
      className: 'navMobileSubTitle',
    },
    {
      name: 'Cancer Genomics Cloud',
      link: '/cgc',
      id: 'navbar-dropdown-item-cancer-genomics-cloud',
      className: 'navMobileSubItem',
    },
    {
      name: 'Database of Genotypes and Phenotypes',
      link: '/dbgap',
      id: 'navbar-dropdown-item-database-of-genotypes-and-phenotypes',
      className: 'navMobileSubItem',
    }],
};
~~~~
This shows how to configure the navbarSublists. Map from a title set in navMobileList either by string, or constant to a list of sublist items.\
**The title from navMobileList must match the key in this map.\
AKA, if you set name = "Example Name" in navMobileList, the mapping in navMobileSublists must have a key of "Example Name": [...]**

## Mobile/Tablet menu configuration
![mobile example](/mobileExample.png "Title")\
This is the About subList from the above example.\
Other Resources has a className of navMobileSubTitle as opposed to navMobileSubItem like the rest. That is the difference.


## Footer Configuration
Head to src/config/globalFooterData.tsx\
The datastructures and what everything does is pretty straight forward.





## Build&RUN

In the project directory, you can run:

### `npm install --legacy-peer-deps`

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

