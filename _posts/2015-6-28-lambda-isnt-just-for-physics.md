---
layout: post
title: Lambda isn't just for physics!
---

When I took the Data Structures class, it was only my second semester of being exposed to programming. We were using Java, since it's very friendly to beginners, although I continued to struggle understanding the programming concepts.

At that time we were working with Java 7, which was released in 2011. It just so happens that around the middle of that semester the developers behind Java released a 20 minute presentation explaining many of the concepts that were to come in the new release of Java 8 a few months later. Hoping it would give me an edge on my classmates, I watched the video. Being a total novice, I found that I hardly understood anything that it was describing; I suppose I sort of expected it to describe low level concepts.

### Lambda Functions

Pretty much all the information discussed went in one ear and out the other for me, but one thing that I managed to catch was the idea of a "lambda" function. In the video, they described the idea as a function that takes another function as one of its arguments. The example they gave was a filter function. Imagine you have a list of objects with various attributes, like color, size, shape and smell. If you wanted to write a function that would return a list of only blue objects, you easily could. Likewise, if you wanted to also have a function that returns only the red objects, you easily could.

```c++
template <typename T>
list<T> filter_blue(const list<T>& master_list){
	list<T> filtered_list;

	// iterate through the list, checking the color
	for (T current : master_list){
		if (current.color == "BLUE"){
			// add it to the new filtered list
			filtered_list.push_back(current);
		}
	}

	return filtered_list;
}
template <typename T>
list<T> filter_red(const list<T>& master_list){
	list<T> filtered_list;

	// iterate through the list, checking the color
	for (T current : master_list){
		if (current.color == "RED"){
			// add it to the new filtered list
			filtered_list.push_back(current);
		}
	}

	return filtered_list;
}
```
#### The Problem
By the time you get to a few different colors you'll end up with several different functions doing practically the same thing. Since code reuse is extremely valuable, such a design would be unattractive.

One obvious solution to this problem is to have a function that expects a list of objects and a second argument that represents the desired color. This is still not ideal, because you'd have to have similar methods for the other attributes (size, shape, smell). Looking at the code below, you can see how these functions become very redundant.

```c++
template <typename T>
list<T> filter_color(const list<T>& master_list, string desired_color){
	list<T> filtered_list;

	// iterate through the list, checking the color
	for (T current : master_list){
		if (current.color == desired_color){
			// add it to the new filtered list
			filtered_list.push_back(current);
		}
	}

	return filtered_list;
}
template <typename T>
list<T> filter_size(const list<T>& master_list, string desired_size){
	list<T> filtered_list;

	// iterate through the list, checking the size
	for (T current : master_list){
		if (current.size == desired_size){
			// add it to the new filtered list
			filtered_list.push_back(current);
		}
	}

	return filtered_list;
}
```

#### The Solution

This is where those lambda functions come into play. By writing a function that takes another function as an argument, it's possible to write ONE filter method that can perform many different tasks. The lambda function should be a binary predicate, meaning it will only return true or false if the object meets some criteria. If the predicate is satisfied, we add the object to the list. If false, we continue iteration.

```c++
template <typename T>
list<T> filter(const list<T>& master_list, std::function<bool(const T&)> filter){
	list<T> filtered_list;

	// iterate through the list, checking the filter
	for (T current : master_list){
		if (filter(current)){
			// add it to the new filtered list
			filtered_list.push_back(current);
		}
	}

	return filtered_list;
}

template <typename T>
void some_function(const list<T>& master_list){
	// get list of all blue objects
	list<T> filtered_color_blue = filter(master_list, [](const T& current)->bool{
		return (current.color == "BLUE");
	});
	// get list of all red objects
	list<T> filtered_color_red = filter(master_list, [](const T& current)->bool{
		return (current.color == "RED");
	});
	// get list of all large objects
	list<T> filtered_color_red = filter(master_list, [](const T& current)->bool{
		return (current.size == "LARGE");
	});
	// get list of all round objects
	list<T> filtered_color_red = filter(master_list, [](const T& current)->bool{
		return (current.shape == "ROUND");
	});
}
```

#### Personal Thoughts

Although the syntax is a little strange to get used to, these lambda functions are really useful for the example of creating a filter, since all of the lambda functions can be passed to the same filter function. This eliminates the need for writing multiple functions that do practically the same task.

I personally think this programming concept is very cool. I first discovered it several years ago, but have never used it until this week when Downing explained them in detail. 



