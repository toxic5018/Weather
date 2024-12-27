<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SVG to PNG Converter</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha3/dist/css/bootstrap.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        body {
            background-color: #f8f9fa;
        }

        .navbar {
            background-color: #343a40;
        }

        .navbar-brand,
        .nav-link {
            color: #fff !important;
        }

        .upload-area {
            border: 2px dashed #3498db;
            border-radius: 10px;
            padding: 30px;
            text-align: center;
            color: #555;
            background: #f9f9f9;
            cursor: pointer;
        }

        .upload-area:hover {
            background-color: #e6f7ff;
        }

        .toast-container {
            position: fixed;
            top: 10px;
            left: 50%;
            transform: translateX(-50%);
            z-index: 1055;
        }

        .processing-text {
            font-style: italic;
        }

        .completed-text {
            color: green;
            font-weight: bold;
        }

        .tutorial-highlight {
            background-color: #cce5ff;
            padding: 10px;
            border-radius: 5px;
            color: #004085;
        }

        .modal-backdrop {
            background-color: rgba(0, 0, 0, 0.3);
        }

        .file-error {
            color: red;
            font-size: 0.9em;
        }

        .modal.fade .modal-dialog {
            transform: translate(0, -50%);
            opacity: 0;
            transition: opacity 0.3s ease, transform 0.3s ease;
        }

        .modal.show .modal-dialog {
            transform: translate(0, 0);
            opacity: 1;
        }

        footer {
            margin-top: 20px;
        }
    </style>
</head>

<body>
    <!-- Toast Container -->
    <div class="toast-container" id="toastContainer"></div>

    <!-- Navbar -->
    <nav class="navbar navbar-expand-lg">
        <div class="container">
            <a class="navbar-brand" href="#">Converter</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav ms-auto">
                    <li class="nav-item">
                        <a class="nav-link" href="#">Home</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link active" href="#">SVG to PNG</a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>

    <!-- Main Content -->
    <div class="container my-5">
        <h1 class="text-center text-primary">SVG to PNG Converter</h1>
        <div class="row mt-3">
            <div class="col-md-6 mx-auto tutorial-highlight">
                <h4>How to Use:</h4>
                <p>1. Click on "Click to fetch image or drop images here" to upload your SVG files.</p>
                <p>2. Convert them to PNG format and download the images.</p>
            </div>
        </div>

        <div class="row mt-4">
            <div class="col-md-12 text-center">
                <div id="uploadArea" class="upload-area">
                    <p><strong>Click to fetch image or drop images here</strong></p>
                </div>
                <button id="clearQueue" class="btn btn-outline-danger mt-3" style="display: none;">Clear Queue</button>
            </div>
        </div>

        <div class="row mt-4">
            <div class="col-md-12">
                <h5 id="fileCount">Uploaded Files (0/20)</h5>
                <ul id="fileList" class="list-group">
                    <!-- Uploaded file names will appear here -->
                </ul>
                <div class="d-flex align-items-center mt-3">
                    <button id="downloadAll" class="btn btn-primary" disabled>Download All</button>
                    <span id="completedStatus" class="ms-3"></span>
                </div>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer class="mt-5 py-3 bg-light text-center">
        <p><strong>What is an SVG to PNG Converter?</strong></p>
        <p>
            An SVG to PNG Converter is a tool that allows you to convert scalable vector graphics (SVG) files into raster images (PNG).
            Simply upload your SVG files, and the converter will generate high-quality PNG files for download.
        </p>
        <p>Website Year: <span id="websiteYear"></span> | ToxicStudios - Do Not Distribute!</p>
        <p>Version: <span id="versionName"></span></p>
    </footer>

    <!-- Back Warning Modal -->
    <div class="modal" id="backWarningModal" tabindex="-1" aria-labelledby="backWarningModalLabel" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="backWarningModalLabel">Are you sure?</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    You will not retrieve the files back if you leave. Do you want to proceed?
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-danger" id="clearQueueModalBtn">Clear</button>
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cancel</button>
                </div>
            </div>
        </div>
    </div>

    <script>
        const version_name = '1.0.0';
        const website_year = 2024;
        document.getElementById('versionName').textContent = version_name;
        document.getElementById('websiteYear').textContent = website_year;

        const uploadArea = document.getElementById('uploadArea');
        const fileList = document.getElementById('fileList');
        const downloadAllButton = document.getElementById('downloadAll');
        const clearQueueButton = document.getElementById('clearQueue');
        const fileCount = document.getElementById('fileCount');
        const completedStatus = document.getElementById('completedStatus');
        const maximum = 20;
        let files = [];
        let completed = 0;

        function updateUI() {
            const current = files.length;
            fileCount.textContent = `Uploaded Files (${current}/${maximum})`;
            clearQueueButton.style.display = current > 0 ? 'inline-block' : 'none';
            downloadAllButton.disabled = current === 0;
            completedStatus.textContent = current === 0 || completed === 0
                ? ''
                : `Completed (${completed}/${files.length})`;
        }

        uploadArea.addEventListener('click', () => {
            const fileInput = document.createElement('input');
            fileInput.type = 'file';
            fileInput.accept = '.svg';
            fileInput.multiple = true;
            fileInput.addEventListener('change', (event) => handleFiles(event.target.files));
            fileInput.click();
        });

        function handleFiles(uploadedFiles) {
            Array.from(uploadedFiles).forEach(file => {
                if (files.length < maximum && file.type === 'image/svg+xml') {
                    files.push(file);
                    const li = document.createElement('li');
                    li.classList.add('list-group-item', 'd-flex', 'justify-content-between', 'align-items-center');

                    const fileName = document.createElement('span');
                    fileName.textContent = file.name;

                    const actions = document.createElement('div');
                    const downloadBtn = document.createElement('button');
                    downloadBtn.classList.add('btn', 'btn-sm', 'btn-dark', 'me-2');
                    downloadBtn.innerHTML = '<i class="fas fa-download"></i>';
                    downloadBtn.addEventListener('click', () => {
                        resetCompleted();
                        startProcessing([li], true);
                    });

                    const deleteBtn = document.createElement('button');
                    deleteBtn.classList.add('btn', 'btn-sm', 'btn-danger');
                    deleteBtn.innerHTML = '<i class="fas fa-trash"></i>';
                    deleteBtn.addEventListener('click', () => deleteFile(file, li));

                    actions.appendChild(downloadBtn);
                    actions.appendChild(deleteBtn);
                    li.appendChild(fileName);
                    li.appendChild(actions);
                    fileList.appendChild(li);
                } else {
                    const li = document.createElement('li');
                    li.classList.add('list-group-item', 'd-flex', 'justify-content-between', 'align-items-center');

                    const fileName = document.createElement('span');
                    fileName.textContent = file.name;

                    const errorText = document.createElement('span');
                    errorText.classList.add('file-error');
                    errorText.textContent = 'Error. Reached Limit (maximum)';

                    li.appendChild(fileName);
                    li.appendChild(errorText);
                    fileList.appendChild(li);
                }
            });
            updateUI();
        }

        function resetCompleted() {
            completed = 0;
            updateUI();
        }

        function startProcessing(listItems, downloadAfter = false) {
            listItems.forEach((li, index) => {
                const actions = li.querySelector('div');
                actions.innerHTML = '<span class="processing-text">Processing (0/100)</span>';
                setTimeout(() => {
                    completed++;
                    actions.innerHTML = '<span class="text-success">Completed</span>';
                    if (downloadAfter) downloadFile(files[index]);
                    updateUI();
                }, 2000); // Simulated processing time
            });
        }

        function downloadFile(file) {
            const link = document.createElement('a');
            link.href = URL.createObjectURL(file); // Simulated processed file URL
            link.download = file.name.replace('.svg', '.png');
            link.click();
            showToast('Download Successful');
        }

        downloadAllButton.addEventListener('click', () => {
            resetCompleted();
            const fileListItems = Array.from(fileList.children);
            startProcessing(fileListItems, true);
        });

        function deleteFile(file, li) {
            files = files.filter(f => f !== file);
            li.remove();
            showToast('Item Removed');
            updateUI();
        }

        function showToast(message) {
            const toast = document.createElement('div');
            toast.classList.add('toast', 'fade', 'show');
            toast.style.position = 'fixed';
            toast.style.top = '10px';
            toast.style.left = '50%';
            toast.style.transform = 'translateX(-50%)';
            toast.classList.add('bg-success', 'text-white');
            toast.innerHTML = message;
            document.body.appendChild(toast);

            setTimeout(() => {
                toast.classList.remove('show');
                document.body.removeChild(toast);
            }, 1500);
        }

        // Modal for warning before clearing queue
        document.getElementById('clearQueue').addEventListener('click', () => {
            const modal = new bootstrap.Modal(document.getElementById('backWarningModal'));
            modal.show();
        });

        document.getElementById('clearQueueModalBtn').addEventListener('click', () => {
            files = [];
            fileList.innerHTML = '';
            completed = 0;
            updateUI();
            showToast('Queue Cleared');
            const modal = bootstrap.Modal.getInstance(document.getElementById('backWarningModal'));
            modal.hide();
        });

        document.querySelector('[data-bs-dismiss="modal"]').addEventListener('click', () => {
            const modal = bootstrap.Modal.getInstance(document.getElementById('backWarningModal'));
            modal.hide();
        });
    </script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha3/dist/js/bootstrap.bundle.min.js"></script>
</body>

</html>
