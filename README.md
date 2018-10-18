# Javascript Object operations


## To clone an object, you can use $.extend or manually add in elements from one object to another one at a time

```shell
const profile = {
  name: 'joh',
  age: 20,
  children: [{
    name: 'pete',
    age: 1,
    toys: ['doll', 'dog']
  },
  {
    name: 'nate',
    age: 2,
    toys: ['apple', 'banana']
  }]
};

const clone = {};

clone.name = profile.name;
clone.age = profile.age;
clone.children = [];

for(let i = 0; i < profile.children.length; i++){
   const newObj = {};
   newObj.name = profile.children[i].name;
   newObj.age = profile.children[i].age;
   newObj.toys = [];
   for(let j = 0; j < profile.children[i].toys.length; j++){
        newObj.toys.push(profile.children[i].toys[j]);
   }
   clone.children.push(newObj);

}
```
You can also add an inner method to the object as well.

For example, you can declare a function for the profile object to get number of toys for each child:

```shell
profile.numToy = function(){
   let strNum = '';

   for(let i = 0; i < this.children.length; i++){
      strNum = strNum + this.children[i].name + ' has ' + this.children[i].toys.length + ' toy(s), ';
   }
   strNum = strNum.substring(0,strNum.length-2) + '.';
   return strNum;

}

```
Here I have created a method to add new children into the children property of the profile object:

```shell
profile.addChildren = function(name, age, toys){
   const child = {};
   child.name = name;
   child.age = age;
   child.toys = [...toys];
   this.children.push(child);
}

profile.addChildren('Peter', 3, ['toy1', 'toy2']);
console.log(profile);
```


