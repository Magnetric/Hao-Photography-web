# Gallery Admin Page

This is a private admin interface for managing your photography galleries with AWS S3 storage. Access it by opening `admin/admin.html` in your browser.

## Features

### Create Galleries
- **Gallery Information**: Add name and description for your gallery
- **Tags System**: Add custom tags like location, year-month, theme, etc.
- **S3 Storage**: Galleries are stored as folders in AWS S3
- **Gallery Management**: Create, edit, and delete galleries
- **Form Validation**: Ensures all required fields are filled

### Upload Photos
- **Gallery Selection**: Choose which gallery to upload photos to
- **Multiple Photo Upload**: Upload single or multiple photos at once
- **Drag & Drop Support**: Drag photos directly onto the upload area
- **Photo Information**: Add title and description for photos
- **Automatic Naming**: Single photos can have custom titles, multiple photos get auto-generated names
- **S3 Upload**: Photos are uploaded directly to AWS S3
- **Automatic Thumbnails**: 300x300 thumbnails are automatically created and stored
- **File Preview**: See preview of all selected photos before uploading
- **Photo Tags**: Add custom tags to individual photos
- **Upload Progress**: Visual progress indicator during S3 upload
- **Duplicate Prevention**: Automatic naming avoids conflicts with existing photos

### Manage Galleries
- **View All Galleries**: See all created galleries in a grid layout
- **Gallery Details**: View name, description, tags, and photo count
- **Edit Galleries**: Click "Edit" to modify gallery details
- **Delete Galleries**: Remove galleries and all their photos from S3

## S3 Storage Structure

### Bucket Organization
```
haophotography/
├── galleries/
│   ├── Europe/
│   │   ├── France/
│   │   │   ├── Paris 2024/
│   │   │   │   ├── metadata.json
│   │   │   │   ├── photo-1.jpg
│   │   │   │   ├── photo-2.jpg
│   │   │   │   └── thumbnails_1/
│   │   │   │       ├── photo-1.jpg
│   │   │   │       └── photo-2.jpg
│   │   │   └── Lyon 2024/
│   │   │       ├── metadata.json
│   │   │       └── photo-1.jpg
│   │   └── Italy/
│   │       ├── Venice 2024/
│   │       │   ├── metadata.json
│   │       │   └── photo-1.jpg
│   ├── Asia/
│   │   ├── Japan/
│   │   │   ├── Tokyo 2023/
│   │   │   │   ├── metadata.json
│   │   │   │   └── photo-1.jpg
│   │   │   └── Kyoto 2023/
│   │   │       ├── metadata.json
│   │   │       └── photo-1.jpg
│   └── North America/
│       ├── United States/
│       │   ├── New York 2024/
│       │   │   ├── metadata.json
│       │   │   └── photo-1.jpg
│       │   └── San Francisco 2024/
│       │       ├── metadata.json
│       │       └── photo-1.jpg
```

### Gallery Metadata
```json
{
    "id": 1234567890,
    "continent": "Europe",
    "country": "France",
    "name": "Paris 2024",
    "description": "Photos from my trip to Paris in 2024",
    "tags": ["Paris", "2024", "Travel", "Architecture"],
    "photos": [...],
    "createdAt": "2024-01-15T10:30:00.000Z"
}
```

### Photo Object
```json
{
    "id": 1234567891,
    "title": "Eiffel Tower",
    "description": "The iconic Eiffel Tower at sunset",
    "image": "https://haophotography.s3.eu-north-1.amazonaws.com/galleries/Paris%202024/photo-1.jpg",
    "thumbnail": "https://haophotography.s3.eu-north-1.amazonaws.com/galleries/Paris%202024/thumbnails_1/photo-1.jpg",
    "tags": ["Architecture", "Sunset", "Iconic"],
    "uploadedAt": "2024-01-15T10:35:00.000Z",
    "s3Key": "galleries/Paris 2024/photo-1.jpg",
    "thumbnailKey": "galleries/Paris 2024/thumbnails_1/photo-1.jpg"
}
```

## How to Use

### 1. Access Admin Page
Open `admin/admin.html` in your web browser.

### 2. Create New Galleries
1. Click the "Create Gallery" tab
2. Fill in the gallery details:
   - **Continent**: Select the continent (e.g., Europe, Asia, North America)
   - **Country**: Select the country from the dropdown
   - **Gallery Name**: Name of your gallery (e.g., "Paris 2024", "Tokyo Streets")
   - **Description**: Detailed description of the gallery (optional)
3. Add tags for organization:
   - **Location tags**: "Paris", "Tokyo", "Swiss Alps"
   - **Time tags**: "2024", "2024-03", "Spring 2024"
   - **Theme tags**: "Landscape", "Portrait", "Street Photography"
4. Click "Create Gallery" to save to S3

### 3. Upload Photos to Galleries
1. Click the "Upload Photos" tab
2. Select the gallery you want to upload to
3. Fill in the photo details:
   - **Photo Title**: Optional for single photos, auto-generated for multiple photos
   - **Photo Description**: Description applied to all photos
4. Upload photos using one of these methods:
   - **Click "Choose File"** to select one or multiple photos
   - **Drag and drop** photos directly onto the upload area
5. Review the preview of selected photos
6. Add photo-specific tags (optional)
7. Click "Upload Photo" to upload to S3

### 4. Manage Existing Galleries
1. Click the "Manage Galleries" tab
2. View all your created galleries
3. Click "Edit" to modify a gallery
4. Click "Delete" to remove a gallery and all its photos from S3

## S3 Configuration

### AWS Credentials
The admin interface is configured with the following S3 settings:
- **Bucket Name**: `haophotography`
- **Region**: `eu-north-1` (Europe - Stockholm)
- **Access Key ID**: `xxxxx`
- **Secret Access Key**: `xxxxx`

### S3 Permissions Required
Your AWS credentials need the following permissions:
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetObject",
                "s3:PutObject",
                "s3:DeleteObject",
                "s3:ListBucket"
            ],
            "Resource": [
                "arn:aws:s3:::haophotography",
                "arn:aws:s3:::haophotography/*"
            ]
        }
    ]
}
```

## Data Storage

- **Galleries**: Stored as folders in S3 with metadata.json files
- **Photos**: Stored directly in S3 with automatic naming (photo-1.jpg, photo-2.jpg, etc.)
- **Thumbnails**: 300x300 thumbnails stored in `thumbnails_1/` subfolder for each gallery
- **Metadata**: Gallery and photo metadata stored in S3
- **URLs**: Photos and thumbnails are accessible via S3 URLs
- **Backup**: All data is stored in AWS S3 with high availability

## Supported File Types

- JPEG (.jpg, .jpeg)
- PNG (.png)
- WebP (.webp)
- GIF (.gif)

## Tips for Best Results

### Gallery Organization
1. **Use Descriptive Names**: "Paris 2024" instead of "Trip 1"
2. **Consistent Tagging**: Use consistent tag formats (e.g., always use "2024" for year)
3. **Location Tags**: Include location in gallery tags for automatic filtering
4. **Year Tags**: Include year in gallery tags for automatic filtering

### Photo Upload
1. **Image Size**: Upload high-resolution images (1200px+ width recommended)
2. **File Size**: Keep files under 10MB for best S3 performance
3. **Descriptive Titles**: Use descriptive titles for your photos
4. **Photo Tags**: Add relevant tags to help organize individual photos

### Tag Suggestions
- **Locations**: "Paris", "Tokyo", "New York", "Swiss Alps"
- **Years**: "2024", "2023", "2022"
- **Months**: "2024-03", "2024-06", "Spring 2024"
- **Themes**: "Landscape", "Portrait", "Street", "Architecture"
- **Colors**: "Black & White", "Color", "Vintage"

## Security Note

This admin page uses AWS credentials directly in the code. For production use:
- Use AWS Cognito for authentication
- Implement pre-signed URLs for secure uploads
- Use IAM roles instead of access keys
- Consider adding basic authentication to the admin page

## Troubleshooting

### S3 Connection Issues
- Check your AWS credentials are correct
- Verify the S3 bucket exists and is accessible
- Check CORS settings on your S3 bucket
- Ensure your AWS credentials have the required permissions

### Upload Failures
- Check file size (should be under 10MB for best performance)
- Verify file format is supported
- Check browser console for detailed error messages
- Ensure you have a stable internet connection

### Galleries Not Loading
- Check S3 bucket permissions
- Verify gallery metadata files exist in S3
- Check browser console for S3 API errors
- Refresh the page to reload from S3

### Photos Not Showing on Main Site
- Photos are automatically converted to the main site format
- Check that gallery tags include location and year information
- Verify S3 URLs are accessible
- Refresh the main site to see new photos

## Integration with Main Site

- Galleries created in admin automatically appear on the main site
- Photos are converted to the format expected by the main gallery
- Location and year are extracted from gallery tags
- S3 URLs are used for photo display
- Changes made in admin are immediately reflected on the main site
- No additional setup required

## Future Enhancements

Potential improvements you could add:
- AWS Cognito authentication
- Pre-signed URLs for secure uploads
- Image optimization and resizing
- CDN integration for faster loading
- Bulk photo upload functionality
- Gallery templates
- Export/import functionality
- Advanced image editing
- SEO optimization tools
- Gallery sharing features 