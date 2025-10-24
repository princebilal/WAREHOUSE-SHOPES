# Database Configuration Guide

## Current Setup
Your main database is working perfectly at:
```
mongodb+srv://testing_db_user:EXMHYtFRbOr9tcbX@cluster0.hpxspu4.mongodb.net/sales_dashboard
```

## Shop Database Configuration

### Option 1: Same Cluster, Different Database (Recommended)
Add this to your environment variables or server configuration:

```bash
SHOP_DATABASE_URI=mongodb+srv://testing_db_user:EXMHYtFRbOr9tcbX@cluster0.hpxspu4.mongodb.net/shop_database?retryWrites=true&w=majority&appName=Cluster0
```

### Option 2: Different Cluster
If you want to use a completely different MongoDB cluster:

```bash
SHOP_DATABASE_URI=mongodb+srv://your_shop_user:your_shop_password@your-shop-cluster.mongodb.net/shop_database?retryWrites=true&w=majority
```

## How to Configure

### Method 1: Environment Variables
Create a `.env` file in your server directory:

```bash
# Main Database (already working)
MONGODB_URI=mongodb+srv://testing_db_user:EXMHYtFRbOr9tcbX@cluster0.hpxspu4.mongodb.net/sales_dashboard?retryWrites=true&w=majority&appName=Cluster0

# Shop Database
SHOP_DATABASE_URI=mongodb+srv://testing_db_user:EXMHYtFRbOr9tcbX@cluster0.hpxspu4.mongodb.net/shop_database?retryWrites=true&w=majority&appName=Cluster0
```

### Method 2: Direct Code Configuration
Update the `getDatabaseUri` method in `server/index.js`:

```javascript
getDatabaseUri(dbName) {
  if (dbName === 'shop') {
    return 'mongodb+srv://testing_db_user:EXMHYtFRbOr9tcbX@cluster0.hpxspu4.mongodb.net/shop_database?retryWrites=true&w=majority&appName=Cluster0';
  }
  // ... rest of the method
}
```

## Database Structure

### Main Database (sales_dashboard)
- Users
- Groups  
- Branches
- Authentication data

### Shop Database (shop_database)
- Shop Categories
- Shop Departments
- Shop Sales
- Shop Settings

## Testing the Configuration

1. Add the shop database URI to your environment
2. Restart your server
3. Check the console logs for:
   ```
   ✅ Shop Database connected successfully!
   ```
4. Test the view switching in your frontend

## Current Status
✅ Main database: Connected and working
✅ Authentication: Working perfectly
✅ View switching: Working (frontend to backend)
⏳ Shop database: Ready to configure
