Ola, como estás?
```

### Generate creative marketing content
```bash
python translatai.py generate --prompt "Write a catchy tagline for a new eco-friendly water bottle"
```

Sample output:
```
"Refresh your world, sustainably."
```

### Using the API in Python
```python
from translatai import Translator, ContentGenerator

# Initialize translator
translator = Translator(api_key="your_openai_api_key")
translated_text = translator.translate("Good morning", source_lang="en", target_lang="fr")
print(translated_text)  # Bonjour

# Generate content
generator = ContentGenerator(api_key="your_openai_api_key")
tagline = generator.generate("Create a slogan for a vegan bakery")
print(tagline)
```

## Contributing

Contributions are welcome! To contribute:

1. Fork the repository.
2. Create your feature branch:
   ```bash
   git checkout -b feature/YourFeature
   ```
3. Commit your changes:
   ```bash
   git commit -m "Add some feature"
   ```
4. Push to the branch:
   ```bash
   git push origin feature/YourFeature
   ```
5. Open a pull request and describe your changes.

Please adhere to the existing code style, write clear commit messages, and include tests where appropriate. For major changes, please open an issue first to discuss.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
```
