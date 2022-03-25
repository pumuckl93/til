---
title: How to customize saving a model from Django Admin
permalink: how-to-customize-saving-a-model-from-django-admin
date: 2022-03-25T15:43:06+01:00
tags:
---

# Django Admin

Django is one of the most famous web frameworks in python. The Django Admin
allows the end user to interact with the Model objects. Most of the time you
don't need to concern yourself, how the model is stored by Django Admin, but
sometimes you want certain actions to happen when a model was updated. e.g. send
a notification, refresh the cache etc. In this case you can customize the
behavior of the Django Admin. Here is a simple example:

```
@admin.register(Book)
class BookAdmin(admin.ModelAdmin):
	# fields
	readonly_fields = ['field_1']


	def save_model(self, request: Any, obj: Any, form: Any, change: Any) -> None:
		# your custome code
		# form.changed_data has the keys of the changed values
		# form.cleaned_data has the actual input values
		# obj is the updated object
		return super().save_model(request, obj, form, change)

```
