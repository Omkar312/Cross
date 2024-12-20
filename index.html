<?php
session_start();

$users_file = "users.txt"; // File to store user credentials
$uploads_dir = "uploads"; // Directory for file uploads
if (!is_dir($uploads_dir)) mkdir($uploads_dir, 0777, true); // Ensure the uploads directory exists

// Initialize variables
$page = isset($_GET['page']) ? $_GET['page'] : 'register';
$message = "";

// Registration Logic
if ($page === 'register' && $_SERVER['REQUEST_METHOD'] === 'POST') {
    $username = $_POST['username'];
    $password = password_hash($_POST['password'], PASSWORD_BCRYPT);

    // Save user credentials
    file_put_contents($users_file, "$username:$password\n", FILE_APPEND);
    $_SESSION['success'] = "Registration successful! Please login.";
    header("Location: index.php?page=login");
    exit();
}

// Login Logic
if ($page === 'login' && $_SERVER['REQUEST_METHOD'] === 'POST') {
    $username = $_POST['username'];
    $password = $_POST['password'];
    $users = file($users_file, FILE_IGNORE_NEW_LINES);

    foreach ($users as $user) {
        list($stored_username, $stored_password) = explode(":", $user);
        if ($stored_username === $username && password_verify($password, $stored_password)) {
            $_SESSION['username'] = $username;
            header("Location: index.php?page=dashboard");
            exit();
        }
    }
    $message = "Invalid username or password.";
}

// File Upload Logic
if ($page === 'dashboard' && $_SERVER['REQUEST_METHOD'] === 'POST' && isset($_FILES['file'])) {
    $file_name = basename($_FILES['file']['name']);
    $target_file = "$uploads_dir/$file_name";

    if (move_uploaded_file($_FILES['file']['tmp_name'], $target_file)) {
        $message = "File uploaded successfully.";
    } else {
        $message = "File upload failed.";
    }
}

// File Delete Logic
if ($page === 'dashboard' && isset($_GET['delete'])) {
    $file_to_delete = "$uploads_dir/" . basename($_GET['delete']);
    if (file_exists($file_to_delete)) {
        unlink($file_to_delete);
        $message = "File deleted successfully.";
    }
}

// Logout Logic
if ($page === 'logout') {
    session_destroy();
    header("Location: index.php?page=login");
    exit();
}

// List of uploaded files
$files = glob("$uploads_dir/*");

?>

<!DOCTYPE html>
<html>
<head>
    <title>File Management System</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <?php if ($page === 'register'): ?>
        <h1>Register</h1>
        <form method="POST" action="index.php?page=register">
            <input type="text" name="username" placeholder="Username" required>
            <input type="password" name="password" placeholder="Password" required>
            <button type="submit">Register</button>
        </form>
        <p>Already have an account? <a href="index.php?page=login">Login here</a></p>

    <?php elseif ($page === 'login'): ?>
        <h1>Login</h1>
        <?php if ($message): ?><p style="color: red;"><?php echo $message; ?></p><?php endif; ?>
        <form method="POST" action="index.php?page=login">
            <input type="text" name="username" placeholder="Username" required>
            <input type="password" name="password" placeholder="Password" required>
            <button type="submit">Login</button>
        </form>
        <p>Don't have an account? <a href="index.php?page=register">Register here</a></p>

    <?php elseif ($page === 'dashboard' && isset($_SESSION['username'])): ?>
        <h1>Welcome, <?php echo htmlspecialchars($_SESSION['username']); ?>!</h1>
        <?php if ($message): ?><p style="color: green;"><?php echo $message; ?></p><?php endif; ?>

        <!-- File Upload -->
        <form method="POST" action="index.php?page=dashboard" enctype="multipart/form-data">
            <input type="file" name="file" required>
            <button type="submit">Upload File</button>
        </form>

        <!-- File List -->
        <h2>Your Files</h2>
        <ul>
            <?php foreach ($files as $file): ?>
                <li>
                    <?php echo basename($file); ?>
                    <a href="<?php echo $file; ?>" download>Download</a>
                    <a href="index.php?page=dashboard&delete=<?php echo basename($file); ?>" style="color: red;">Delete</a>
                </li>
            <?php endforeach; ?>
        </ul>

        <!-- Logout -->
        <a href="index.php?page=logout"><button>Logout</button></a>

    <?php else: ?>
        <?php header("Location: index.php?page=login"); ?>
    <?php endif; ?>
</body>
</html>
