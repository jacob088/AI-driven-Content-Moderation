# AI-driven-Content-Moderation
Développez un système de modération de contenu alimenté par l'IA pour les plateformes de médias sociaux, afin de détecter et de supprimer le contenu inapproprié ou offensant.
import re

# Sample data: List of posts (in a real scenario, you would fetch this from your database or social media platform)
posts = [
    "I love this beautiful day!",
    "This is a terrible and disgusting act!",
    "Enjoying the lovely weather with friends :)",
    "I can't stand the filthy language some people use!!!",
]

# List of offensive keywords for demonstration purposes (in real scenarios, this list would be much more comprehensive and nuanced)
offensive_keywords = ["terrible", "disgusting", "filthy"]

def is_content_appropriate(post, offensive_keywords):
    """
    Check if the post is appropriate by searching for offensive keywords.
    
    :param post: The social media post (text) to be checked.
    :param offensive_keywords: A list of keywords considered offensive.
    :return: True if the post is considered appropriate, False otherwise.
    """
    # Normalize the post to lowercase to ensure the comparison catches all matches
    post_lower = post.lower()
    
    # Check if any of the offensive keywords are in the post
    for keyword in offensive_keywords:
        if re.search(r'\b' + keyword + r'\b', post_lower):
            return False
    return True

# Filter the posts
appropriate_posts = [post for post in posts if is_content_appropriate(post, offensive_keywords)]

# Display the results
print("Appropriate Posts:")
for post in appropriate_posts:
    print(f"- {post}")
