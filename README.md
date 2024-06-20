from django.db import models
from django.contrib.auth.models import AbstractBaseUser, BaseUserManager

class UserManager(BaseUserManager):
    def create_user(self, email, password=None, **extra_fields):
        # ... (code for creating user)

    def create_superuser(self, email, password, **extra_fields):
        # ... (code for creating superuser)

class User(AbstractBaseUser):
    email = models.EmailField(unique=True)
    name = models.CharField(max_length=255, blank=True)
    # ... (add any additional fields)

    USERNAME_FIELD = 'email'
    REQUIRED_FIELDS = []

    objects = UserManager()

    def _str_(self):
        return self.email
        AUTH_USER_MODEL = 'users.User'    from django import forms
from django.contrib.auth import authenticate

class LoginForm(forms.Form):
    email = forms.EmailField(label='Email Address')
    password = forms.CharField(widget=forms.PasswordInput)

    def clean(self):
        cleaned_data = super().clean()
        email = cleaned_data.get('email')
        password = cleaned_data.get('password')

        if email and password:
            user = authenticate(email=email, password=password)
            if not user:
                raise forms.ValidationError('Invalid email or password.')
        return cleaned_data
