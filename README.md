# 光致星联-三维与平面效果图展示
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>光致星联-三维与平面效果图展示</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', 'Microsoft YaHei', sans-serif;
        }
        
        body {
            background-color: #f8fafc;
            color: #333;
            line-height: 1.6;
            padding: 20px;
        }
        
        .container {
            max-width: 1400px;
            margin: 0 auto;
        }
        
        header {
            text-align: center;
            margin-bottom: 30px;
            padding: 20px;
            background: linear-gradient(135deg, #1a237e 0%, #283593 100%);
            color: white;
            border-radius: 12px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        h1 {
            font-size: 2.4rem;
            margin-bottom: 8px;
        }
        
        .subtitle {
            font-size: 1.1rem;
            opacity: 0.9;
        }
        
        .content-wrapper {
            display: flex;
            flex-wrap: wrap;
            gap: 30px;
            margin-bottom: 40px;
        }
        
        .viewer-container {
            flex: 1;
            min-width: 300px;
        }
        
        .viewer-title {
            display: flex;
            align-items: center;
            background-color: #1a237e;
            color: white;
            padding: 15px 20px;
            border-radius: 10px 10px 0 0;
            font-weight: 600;
        }
        
        .viewer-title i {
            margin-right: 10px;
            font-size: 1.2rem;
        }
        
        .viewer {
            height: 500px;
            background-color: white;
            border-radius: 0 0 10px 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.08);
        }
        
        .viewer iframe {
            width: 100%;
            height: 100%;
            border: none;
        }
        
        .viewer img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            display: block;
        }
        
        .info-panel {
            background-color: white;
            border-radius: 12px;
            padding: 30px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.08);
            margin-bottom: 30px;
        }
        
        .info-title {
            color: #1a237e;
            font-size: 1.8rem;
            margin-bottom: 25px;
            padding-bottom: 10px;
            border-bottom: 2px solid #e8eaf6;
            display: flex;
            align-items: center;
        }
        
        .info-title i {
            margin-right: 12px;
        }
        
        .info-columns {
            display: flex;
            flex-wrap: wrap;
            gap: 30px;
        }
        
        .info-column {
            flex: 1;
            min-width: 300px;
        }
        
        .info-column h3 {
            color: #283593;
            margin-bottom: 15px;
            font-size: 1.3rem;
            display: flex;
            align-items: center;
        }
        
        .info-column h3 i {
            margin-right: 10px;
            color: #3949ab;
        }
        
        .info-list {
            list-style-type: none;
        }
        
        .info-list li {
            padding: 12px 15px;
            margin-bottom: 10px;
            background-color: #f5f7ff;
            border-radius: 8px;
            border-left: 4px solid #3949ab;
            transition: transform 0.2s, background-color 0.2s;
        }
        
        .info-list li:hover {
            transform: translateX(5px);
            background-color: #e8eaf6;
        }
        
        .material-list {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 15px;
        }
        
        .material-item {
            background-color: #f5f7ff;
            padding: 20px;
            border-radius: 10px;
            border: 1px solid #e8eaf6;
            transition: transform 0.2s, box-shadow 0.2s;
        }
        
        .material-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px rgba(57, 73, 171, 0.15);
        }
        
        .material-name {
            font-weight: 600;
            color: #283593;
            margin-bottom: 8px;
            font-size: 1.1rem;
        }
        
        .material-desc {
            color: #555;
            font-size: 0.95rem;
        }
        
        footer {
            text-align: center;
            padding: 20px;
            margin-top: 20px;
            color: #666;
            border-top: 1px solid #e0e0e0;
        }
        
        @media (max-width: 768px) {
            .content-wrapper {
                flex-direction: column;
            }
            
            .viewer {
                height: 400px;
            }
            
            h1 {
                font-size: 1.8rem;
            }
        }
        
        .loading {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100%;
            color: #666;
            font-size: 1.1rem;
        }
        
        .loading i {
            margin-right: 10px;
            color: #3949ab;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>光致星联-三维与平面效果图展示</h1>
            <p class="subtitle">项目编号：1-12-19（镜像） | 设计者：Li-Ming-limingChen</p>
        </header>
        
        <div class="content-wrapper">
            <div class="viewer-container">
                <div class="viewer-title">
                    <i class="fas fa-cube"></i> 三维效果图 (交互式视图)
                </div>
                <div class="viewer" id="viewer-3d">
                    <div class="loading">
                        <i class="fas fa-spinner fa-spin"></i> 正在加载3D模型...
                    </div>
                </div>
            </div>
            
            <div class="viewer-container">
                <div class="viewer-title">
                    <i class="fas fa-image"></i> 平面效果图
                </div>
                <div class="viewer" id="viewer-2d">
                    <div class="loading">
                        <i class="fas fa-spinner fa-spin"></i> 正在加载平面效果图...
                    </div>
                </div>
            </div>
        </div>
        
        <div class="info-panel">
            <h2 class="info-title"><i class="fas fa-clipboard-list"></i> 施工注意事项与材质说明</h2>
            
            <div class="info-columns">
                <div class="info-column">
                    <h3><i class="fas fa-hard-hat"></i> 施工注意事项</h3>
                    <ul class="info-list">
                        <li>施工前必须仔细核对设计图纸与现场尺寸，确保无误后方可开始施工。</li>
                        <li>所有材料进场前需进行严格检查，确保符合设计要求的规格和质量标准。</li>
                        <li>钢架结构焊接处必须进行防锈处理，焊缝应平整、无气泡、无夹渣。</li>
                        <li>灯光系统安装需按照电路图进行，确保所有线路绝缘良好，接地可靠。</li>
                        <li>玻璃安装时应使用专用吸盘，确保玻璃表面无划痕，安装后需检查牢固性。</li>
                        <li>曲面结构部分施工时需使用专用模具，确保弧度与设计完全一致。</li>
                        <li>施工过程中必须做好安全防护措施，高空作业需系好安全带。</li>
                        <li>完工后需进行整体清洁，确保表面无污渍、无施工残留物。</li>
                    </ul>
                </div>
                
                <div class="info-column">
                    <h3><i class="fas fa-palette"></i> 材质说明</h3>
                    <div class="material-list">
                        <div class="material-item">
                            <div class="material-name">镜面不锈钢</div>
                            <div class="material-desc">厚度2.0mm，表面8K镜面处理，用于主体结构框架，提供高反射效果。</div>
                        </div>
                        <div class="material-item">
                            <div class="material-name">超白钢化玻璃</div>
                            <div class="material-desc">厚度12mm，透光率≥91%，用于观景平台及围护结构，提供优良视野。</div>
                        </div>
                        <div class="material-item">
                            <div class="material-name">LED光带</div>
                            <div class="material-desc">RGBW四色可变，IP67防水等级，用于夜间照明及氛围营造。</div>
                        </div>
                        <div class="material-item">
                            <div class="material-name">碳纤维复合材料</div>
                            <div class="material-desc">用于曲面结构部分，强度高、重量轻，表面哑光处理。</div>
                        </div>
                        <div class="material-item">
                            <div class="material-name">防滑玻璃地板</div>
                            <div class="material-desc">厚度15mm，表面微晶防滑处理，承载能力≥500kg/m²。</div>
                        </div>
                        <div class="material-item">
                            <div class="material-name">铝合金型材</div>
                            <div class="material-desc">6063-T5航空铝材，阳极氧化处理，用于连接件及辅助支撑。</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        
        <footer>
            <p>© 2023 光致星联设计项目 | 三维模型来源：Sketchfab - Li-Ming-limingChen | 平面效果图来源：项目设计图</p>
            <p>本页面为设计展示用途，实际施工请以最终审批图纸为准。</p>
        </footer>
    </div>

    <script>
        // 加载3D模型
        document.addEventListener('DOMContentLoaded', function() {
            // 3D模型嵌入代码
            const sketchfabEmbed = `
            <iframe title="光致星联-1-12-19（镜像）✔-三维视图-{三维}" frameborder="0" allowfullscreen mozallowfullscreen="true" 
                webkitallowfullscreen="true" allow="autoplay; fullscreen; xr-spatial-tracking" xr-spatial-tracking 
                execution-while-out-of-viewport execution-while-not-rendered web-share 
                src="https://sketchfab.com/models/92d70090841048f38a5e9bcb43c2d6cb/embed?autospin=1&autostart=1">
            </iframe>
            `;
            
            // 平面效果图URL
            const imageUrl = "https://image2url.com/r2/bucket3/images/1767776083426-77ba21c2-433f-4e06-8e31-d5ae74ebdf16.png";
            
            // 设置3D模型iframe
            const viewer3d = document.getElementById('viewer-3d');
            setTimeout(() => {
                viewer3d.innerHTML = sketchfabEmbed;
            }, 800);
            
            // 设置平面效果图
            const viewer2d = document.getElementById('viewer-2d');
            setTimeout(() => {
                viewer2d.innerHTML = `<img src="${imageUrl}" alt="光致星联平面效果图" onerror="this.onerror=null; this.parentElement.innerHTML='<div class=\'loading\'><i class=\'fas fa-exclamation-triangle\'></i> 图片加载失败，请检查链接</div>';" />`;
            }, 1200);
            
            // 为列表项添加点击效果
            const listItems = document.querySelectorAll('.info-list li');
            listItems.forEach(item => {
                item.addEventListener('click', function() {
                    this.style.backgroundColor = '#e3f2fd';
                    setTimeout(() => {
                        this.style.backgroundColor = '';
                    }, 300);
                });
            });
        });
    </script>
</body>
</html>
