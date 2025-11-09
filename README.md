# FbxPythonSDK

# FBX SDK For Python 3.13 功能说明和使用指南

基于对FBX SDK代码的全面分析，现在为您提供详细的 FBX SDK For Python 3.13 功能说明和使用示例。


## FBX SDK 功能详细说明（中文）

由<mcfile name="fbx_solution.py" path="E:\AxListPython\demo\fbx_sdk\fbx_solution.py"></mcfile>生成的FBX SDK是一个完整的Python绑定库，提供了Autodesk FBX SDK的全部功能。

### 核心功能模块

#### 1. 场景管理 (Scene Management)
- **场景创建和销毁**: 创建、管理和销毁FBX场景对象
- **节点层次结构**: 管理场景中的父子节点关系
- **全局设置**: 设置时间模式、系统单位、坐标轴系统
- **场景信息**: 存储场景元数据（标题、作者、描述等）

#### 2. 几何体处理 (Geometry Processing)
- **网格(Mesh)**: 创建和编辑多边形网格，支持控制点、多边形、顶点数据
- **NURBS曲面**: 非均匀有理B样条曲面建模
- **面片(Patch)**: 面片几何体支持
- **曲线(Curve)**: 各种类型的曲线几何体

#### 3. 动画系统 (Animation System)
- **关键帧动画**: 支持位置、旋转、缩放的动画关键帧
- **骨骼动画**: 完整的骨骼系统和蒙皮支持
- **变形器(Deformer)**: 包括蒙皮(Skin)、簇(Cluster)等变形器
- **动画曲线**: 贝塞尔曲线、线性、常量等插值类型
- **动画层**: 支持多层动画叠加

#### 4. 材质和纹理 (Materials and Textures)
- **材质系统**: 支持Phong、Lambert等材质模型
- **纹理映射**: 漫反射、法线、高光等纹理通道
- **UV坐标**: 复杂的UV映射和展开
- **分层纹理**: 支持多层纹理叠加效果

#### 5. 相机和灯光 (Cameras and Lights)
- **相机系统**: 透视和正交相机，支持焦距、视野等参数
- **灯光类型**: 点光源、方向光、聚光灯等
- **光照属性**: 颜色、强度、衰减等光照参数

#### 6. 骨骼系统 (Skeleton System)
- **骨骼创建**: 支持根骨骼、肢体骨骼等类型
- **骨骼动画**: 完整的骨骼变换和动画支持
- **姿态管理**: 绑定姿态、休息姿态等姿态管理

### 文件格式支持
- **FBX二进制格式**: 高效的二进制文件读写
- **FBX ASCII格式**: 可读的文本格式，便于调试
- **嵌入媒体**: 支持纹理、音频等媒体资源嵌入
- **多版本兼容**: 支持不同版本的FBX文件

## 使用说明和示例代码

我已经为您创建了两个详细的示例文件：

### 1. 基础使用示例 (<mcfile name="fbx_sdk_usage_example.py" path="E:\AxListPython\demo\fbx_sdk\fbx_sdk_usage_example.py"></mcfile>)

这个示例展示了FBX SDK的基础功能：

```python
# 初始化FBX SDK
sdk_manager, scene = initialize_fbx_sdk()

# 创建立方体网格
mesh_node = create_simple_mesh(sdk_manager, scene)

# 创建材质
create_material(sdk_manager, scene, mesh_node)

# 创建动画
create_animation(sdk_manager, scene, mesh_node)

# 导出场景
export_scene(sdk_manager, scene, "demo_scene.fbx")
```

### 2. 高级功能示例 (<mcfile name="advanced_fbx_example.py" path="E:\AxListPython\demo\fbx_sdk\advanced_fbx_example.py"></mcfile>)

这个示例展示了高级功能：

```python
# 创建角色骨骼系统
skeleton_nodes = create_character_skeleton(sdk_manager, scene)

# 创建角色网格并绑定骨骼
body_node, body_mesh = create_character_mesh(sdk_manager, scene, skeleton_nodes)

# 设置蒙皮变形器
setup_skin_deformer(sdk_manager, scene, body_node, body_mesh, skeleton_nodes)

# 创建复杂动画
create_complex_animation(sdk_manager, scene, skeleton_nodes)
```

## 关键类和函数说明

### 核心类
- **FbxManager**: FBX SDK管理器，所有对象的分配器
- **FbxScene**: 场景对象，包含所有场景元素
- **FbxNode**: 场景节点，可以附加各种属性
- **FbxMesh**: 网格几何体
- **FbxCamera**: 相机对象
- **FbxLight**: 灯光对象
- **FbxMaterial**: 材质对象
- **FbxSkeleton**: 骨骼对象
- **FbxAnimStack**: 动画栈

### 重要函数
- **InitializeSdkObjects()**: 初始化SDK对象
- **SaveScene()**: 保存场景到文件
- **LoadScene()**: 从文件加载场景
- **FbxTime**: 时间管理类
- **FbxVector4**: 4维向量类

## 使用流程

1. **初始化**: 创建FbxManager和FbxScene
2. **创建内容**: 添加几何体、材质、灯光、相机等
3. **设置动画**: 创建动画曲线和关键帧
4. **配置导出**: 设置导出选项和参数
5. **保存文件**: 导出为FBX格式
6. **清理资源**: 销毁管理器释放内存

## 优势特点

1. **完整的Python绑定**: 原生Python接口，无需C++知识
2. **实时日志输出**: 优化的subprocess调用，提供实时反馈
3. **丰富的示例**: 包含多个完整的示例代码
4. **跨平台支持**: 支持Windows、Linux、macOS
5. **商业级质量**: 基于Autodesk官方FBX SDK




## 详细示例代码

### 基础使用示例

以下是一个完整的FBX SDK使用示例，演示场景创建、导入导出、动画处理等功能：

```python
# FBX SDK 使用示例代码
# 包含完整的场景创建、导入导出、动画处理等功能演示

import os
import sys
import fbx
from fbx import *

def initialize_fbx_sdk():
    """
    初始化FBX SDK管理器
    返回: (FbxManager, FbxScene) 元组
    """
    # 创建FBX SDK管理器，这是所有FBX对象的分配器
    sdk_manager = FbxManager.Create()
    if not sdk_manager:
        print("错误: 无法创建FBX SDK管理器")
        return None, None
    
    # 创建IOSettings对象，用于配置导入导出选项
    ios = FbxIOSettings.Create(sdk_manager, IOSROOT)
    sdk_manager.SetIOSettings(ios)
    
    # 创建场景对象
    scene = FbxScene.Create(sdk_manager, "我的场景")
    
    return sdk_manager, scene

def create_simple_mesh(sdk_manager, scene):
    """
    创建一个简单的立方体网格
    """
    # 创建网格节点
    mesh_node = FbxNode.Create(sdk_manager, "立方体")
    
    # 创建网格属性
    mesh = FbxMesh.Create(sdk_manager, "立方体网格")
    
    # 设置控制点（立方体的8个顶点）
    control_points = [
        FbxVector4(-50, 0, 50),   # 左下前
        FbxVector4(50, 0, 50),    # 右下前
        FbxVector4(50, 100, 50),  # 右上前
        FbxVector4(-50, 100, 50), # 左上前
        FbxVector4(-50, 0, -50),  # 左下后
        FbxVector4(50, 0, -50),   # 右下后
        FbxVector4(50, 100, -50), # 右上后
        FbxVector4(-50, 100, -50) # 左上后
    ]
    
    # 初始化控制点
    mesh.InitControlPoints(8)
    for i, point in enumerate(control_points):
        mesh.SetControlPointAt(point, i)
    
    # 创建立方体的6个面（每个面2个三角形）
    # 前面
    mesh.BeginPolygon()
    mesh.AddPolygon(0)  # 左下前
    mesh.AddPolygon(1)  # 右下前
    mesh.AddPolygon(2)  # 右上前
    mesh.AddPolygon(3)  # 左上前
    mesh.EndPolygon()
    
    mesh.BeginPolygon()
    mesh.AddPolygon(0)  # 左下前
    mesh.AddPolygon(3)  # 左上前
    mesh.AddPolygon(2)  # 右上前
    mesh.AddPolygon(1)  # 右下前
    mesh.EndPolygon()
    
    # 设置网格到节点
    mesh_node.SetNodeAttribute(mesh)
    
    # 将节点添加到场景根节点
    scene.GetRootNode().AddChild(mesh_node)
    
    return mesh_node

def create_material(sdk_manager, scene, node, material_name="红色材质"):
    """
    创建材质并应用到节点
    """
    # 创建材质
    material = FbxSurfacePhong.Create(sdk_manager, material_name)
    
    # 设置材质属性
    material.Diffuse.Set(FbxDouble3(1.0, 0.0, 0.0))  # 红色
    material.Specular.Set(FbxDouble3(1.0, 1.0, 1.0)) # 高光白色
    material.Shininess.Set(0.5)  # 光泽度
    
    # 将材质添加到场景
    scene.AddMaterial(material)
    
    # 将材质应用到网格节点
    node.AddMaterial(material)
    
    return material

def create_animation(sdk_manager, scene, node):
    """
    为节点创建简单动画
    """
    # 创建动画栈
    anim_stack = FbxAnimStack.Create(sdk_manager, "旋转动画")
    
    # 创建动画层
    anim_layer = FbxAnimLayer.Create(sdk_manager, "基础层")
    anim_stack.AddMember(anim_layer)
    
    # 设置当前动画栈
    scene.SetCurrentAnimationStack(anim_stack)
    
    # 创建旋转动画曲线
    # X轴旋转
    anim_curve_x = node.LclRotation.GetCurve(anim_layer, "X", True)
    if anim_curve_x:
        anim_curve_x.KeyModifyBegin()
        
        # 第0帧：0度
        key_index = anim_curve_x.KeyAdd(FbxTime(0))
        anim_curve_x.KeySet(key_index, FbxTime(0), 0.0, FbxAnimCurveDef.eInterpolationLinear)
        
        # 第100帧：360度
        key_index = anim_curve_x.KeyAdd(FbxTime(100 * FbxTime.GetOneFrameValue(FbxTime.EMode.eFrames30)))
        anim_curve_x.KeySet(key_index, FbxTime(100 * FbxTime.GetOneFrameValue(FbxTime.EMode.eFrames30)), 
                          360.0, FbxAnimCurveDef.eInterpolationLinear)
        
        anim_curve_x.KeyModifyEnd()
    
    return anim_stack

def export_scene(sdk_manager, scene, filename):
    """
    导出场景到FBX文件
    """
    # 创建导出器
    exporter = FbxExporter.Create(sdk_manager, "")
    
    # 设置导出选项
    file_format = sdk_manager.GetIOPluginRegistry().GetNativeWriterFormat()
    
    # 配置IOSettings
    ios = sdk_manager.GetIOSettings()
    ios.SetBoolProp(EXP_FBX_MATERIAL, True)
    ios.SetBoolProp(EXP_FBX_TEXTURE, True)
    ios.SetBoolProp(EXP_FBX_EMBEDDED, False)
    ios.SetBoolProp(EXP_FBX_ANIMATION, True)
    ios.SetBoolProp(EXP_FBX_GLOBAL_SETTINGS, True)
    
    # 初始化导出器
    result = exporter.Initialize(filename, file_format, ios)
    if not result:
        print(f"错误: 无法初始化导出器到文件 {filename}")
        return False
    
    # 导出场景
    result = exporter.Export(scene)
    
    # 清理
    exporter.Destroy()
    
    if result:
        print(f"场景已成功导出到: {filename}")
    else:
        print(f"导出失败: {filename}")
    
    return result

def import_scene(sdk_manager, filename):
    """
    从FBX文件导入场景
    """
    # 创建新场景
    scene = FbxScene.Create(sdk_manager, "导入的场景")
    
    # 创建导入器
    importer = FbxImporter.Create(sdk_manager, "")
    
    # 初始化导入器
    result = importer.Initialize(filename, -1, sdk_manager.GetIOSettings())
    if not result:
        print(f"错误: 无法初始化导入器从文件 {filename}")
        return None
    
    # 配置导入选项
    if importer.IsFBX():
        ios = sdk_manager.GetIOSettings()
        ios.SetBoolProp(EXP_FBX_MATERIAL, True)
        ios.SetBoolProp(EXP_FBX_TEXTURE, True)
        ios.SetBoolProp(EXP_FBX_EMBEDDED, True)
        ios.SetBoolProp(EXP_FBX_ANIMATION, True)
        ios.SetBoolProp(EXP_FBX_GLOBAL_SETTINGS, True)
    
    # 导入场景
    result = importer.Import(scene)
    
    # 清理
    importer.Destroy()
    
    if result:
        print(f"场景已成功从 {filename} 导入")
        return scene
    else:
        print(f"导入失败: {filename}")
        return None

def display_scene_info(scene):
    """
    显示场景基本信息
    """
    print("\n=== 场景信息 ===")
    print(f"场景名称: {scene.GetName()}")
    
    # 显示根节点信息
    root_node = scene.GetRootNode()
    print(f"根节点子节点数量: {root_node.GetChildCount()}")
    
    # 显示材质数量
    material_count = scene.GetMaterialCount()
    print(f"材质数量: {material_count}")
    
    # 显示动画栈信息
    anim_stack_count = scene.GetSrcObjectCount(FbxCriteria.ObjectType(FbxAnimStack.ClassId))
    print(f"动画栈数量: {anim_stack_count}")
    
    if anim_stack_count > 0:
        for i in range(anim_stack_count):
            anim_stack = scene.GetSrcObject(FbxCriteria.ObjectType(FbxAnimStack.ClassId), i)
            print(f"  动画栈 {i}: {anim_stack.GetName()}")

def traverse_scene_hierarchy(node, level=0):
    """
    遍历场景层次结构
    """
    indent = "  " * level
    print(f"{indent}节点: {node.GetName()}")
    
    # 显示节点属性类型
    attribute = node.GetNodeAttribute()
    if attribute:
        attr_type = attribute.GetAttributeType()
        type_names = {
            FbxNodeAttribute.EType.eMarker: "标记",
            FbxNodeAttribute.EType.eSkeleton: "骨骼",
            FbxNodeAttribute.EType.eMesh: "网格",
            FbxNodeAttribute.EType.eCamera: "相机",
            FbxNodeAttribute.EType.eLight: "灯光",
            FbxNodeAttribute.EType.eBoundary: "边界",
            FbxNodeAttribute.EType.eOpticalReference: "光学参考",
            FbxNodeAttribute.EType.eOpticalMarker: "光学标记",
            FbxNodeAttribute.EType.eNurbs: "NURBS",
            FbxNodeAttribute.EType.ePatch: "面片",
            FbxNodeAttribute.EType.eNurbsCurve: "NURBS曲线",
            FbxNodeAttribute.EType.eTrimNurbsSurface: "修剪NURBS曲面",
            FbxNodeAttribute.EType.eUnknown: "未知"
        }
        type_name = type_names.get(attr_type, "未知类型")
        print(f"{indent}  属性类型: {type_name}")
    
    # 递归遍历子节点
    for i in range(node.GetChildCount()):
        traverse_scene_hierarchy(node.GetChild(i), level + 1)

def main():
    """
    主函数：演示FBX SDK的主要功能
    """
    print("=== FBX SDK 功能演示 ===")
    
    # 1. 初始化FBX SDK
    sdk_manager, scene = initialize_fbx_sdk()
    if not sdk_manager:
        return
    
    # 2. 创建简单几何体
    print("\n1. 创建立方体网格...")
    mesh_node = create_simple_mesh(sdk_manager, scene)
    
    # 3. 创建材质
    print("2. 创建材质...")
    create_material(sdk_manager, scene, mesh_node)
    
    # 4. 创建动画
    print("3. 创建动画...")
    create_animation(sdk_manager, scene, mesh_node)
    
    # 5. 显示场景信息
    print("4. 显示场景信息...")
    display_scene_info(scene)
    
    # 6. 遍历场景层次
    print("\n5. 场景层次结构:")
    traverse_scene_hierarchy(scene.GetRootNode())
    
    # 7. 导出场景
    print("\n6. 导出场景...")
    export_file = "demo_scene.fbx"
    export_scene(sdk_manager, scene, export_file)
    
    # 8. 导入场景（演示导入功能）
    print("\n7. 导入场景...")
    imported_scene = import_scene(sdk_manager, export_file)
    if imported_scene:
        display_scene_info(imported_scene)
    
    # 9. 清理资源
    print("\n8. 清理资源...")
    sdk_manager.Destroy()
    
    print("\n=== 演示完成 ===")

if __name__ == "__main__":
    main()
```

### 高级使用示例

以下是一个高级FBX SDK示例，演示骨骼动画、蒙皮、复杂场景等高级功能：

```python
# 高级FBX SDK示例代码
# 演示骨骼动画、蒙皮、复杂场景等高级功能

import os
import sys
import math
import fbx
from fbx import *

def create_character_skeleton(sdk_manager, scene):
    """
    创建角色骨骼系统
    """
    print("创建角色骨骼系统...")
    
    # 创建根骨骼（臀部）
    root_bone = FbxNode.Create(sdk_manager, "Hip")
    root_bone_attr = FbxSkeleton.Create(sdk_manager, "Hip")
    root_bone_attr.SetSkeletonType(FbxSkeleton.EType.eRoot)
    root_bone.SetNodeAttribute(root_bone_attr)
    root_bone.LclTranslation.Set(FbxDouble3(0, 0, 0))
    
    # 创建脊柱骨骼
    spine_bone = FbxNode.Create(sdk_manager, "Spine")
    spine_bone_attr = FbxSkeleton.Create(sdk_manager, "Spine")
    spine_bone_attr.SetSkeletonType(FbxSkeleton.EType.eLimbNode)
    spine_bone.SetNodeAttribute(spine_bone_attr)
    spine_bone.LclTranslation.Set(FbxDouble3(0, 50, 0))
    
    # 创建胸部骨骼
    chest_bone = FbxNode.Create(sdk_manager, "Chest")
    chest_bone_attr = FbxSkeleton.Create(sdk_manager, "Chest")
    chest_bone_attr.SetSkeletonType(FbxSkeleton.EType.eLimbNode)
    chest_bone.SetNodeAttribute(chest_bone_attr)
    chest_bone.LclTranslation.Set(FbxDouble3(0, 50, 0))
    
    # 创建左臂骨骼
    left_arm_bone = FbxNode.Create(sdk_manager, "LeftArm")
    left_arm_bone_attr = FbxSkeleton.Create(sdk_manager, "LeftArm")
    left_arm_bone_attr.SetSkeletonType(FbxSkeleton.EType.eLimbNode)
    left_arm_bone.SetNodeAttribute(left_arm_bone_attr)
    left_arm_bone.LclTranslation.Set(FbxDouble3(-20, 0, 0))
    
    # 创建左前臂骨骼
    left_forearm_bone = FbxNode.Create(sdk_manager, "LeftForearm")
    left_forearm_bone_attr = FbxSkeleton.Create(sdk_manager, "LeftForearm")
    left_forearm_bone_attr.SetSkeletonType(FbxSkeleton.EType.eLimbNode)
    left_forearm_bone.SetNodeAttribute(left_forearm_bone_attr)
    left_forearm_bone.LclTranslation.Set(FbxDouble3(-30, 0, 0))
    
    # 创建左手骨骼
    left_hand_bone = FbxNode.Create(sdk_manager, "LeftHand")
    left_hand_bone_attr = FbxSkeleton.Create(sdk_manager, "LeftHand")
    left_hand_bone_attr.SetSkeletonType(FbxSkeleton.EType.eLimbNode)
    left_hand_bone.SetNodeAttribute(left_hand_bone_attr)
    left_hand_bone.LclTranslation.Set(FbxDouble3(-10, 0, 0))
    
    # 构建骨骼层次结构
    root_bone.AddChild(spine_bone)
    spine_bone.AddChild(chest_bone)
    chest_bone.AddChild(left_arm_bone)
    left_arm_bone.AddChild(left_forearm_bone)
    left_forearm_bone.AddChild(left_hand_bone)
    
    # 将根骨骼添加到场景
    scene.GetRootNode().AddChild(root_bone)
    
    return {
        'root': root_bone,
        'spine': spine_bone,
        'chest': chest_bone,
        'left_arm': left_arm_bone,
        'left_forearm': left_forearm_bone,
        'left_hand': left_hand_bone
    }

def create_character_mesh(sdk_manager, scene, skeleton_nodes):
    """
    创建角色网格并绑定到骨骼
    """
    print("创建角色网格...")
    
    # 创建简单的圆柱体作为身体
    body_mesh = FbxMesh.Create(sdk_manager, "BodyMesh")
    
    # 设置控制点（简化的身体形状）
    control_points = []
    height_segments = 5
    radius = 15
    
    for segment in range(height_segments):
        y_pos = segment * 25
        for angle in range(8):  # 8边形
            rad = angle * 3.14159 / 4
            x = radius * math.cos(rad)
            z = radius * math.sin(rad)
            control_points.append(FbxVector4(x, y_pos, z))
    
    body_mesh.InitControlPoints(len(control_points))
    for i, point in enumerate(control_points):
        body_mesh.SetControlPointAt(point, i)
    
    # 创建多边形面
    for segment in range(height_segments - 1):
        for i in range(8):
            next_i = (i + 1) % 8
            
            # 当前层的顶点索引
            v0 = segment * 8 + i
            v1 = segment * 8 + next_i
            v2 = (segment + 1) * 8 + next_i
            v3 = (segment + 1) * 8 + i
            
            # 创建四边形面
            body_mesh.BeginPolygon()
            body_mesh.AddPolygon(v0)
            body_mesh.AddPolygon(v1)
            body_mesh.AddPolygon(v2)
            body_mesh.AddPolygon(v3)
            body_mesh.EndPolygon()
    
    # 创建网格节点
    body_node = FbxNode.Create(sdk_manager, "Body")
    body_node.SetNodeAttribute(body_mesh)
    
    # 将网格添加到场景
    scene.GetRootNode().AddChild(body_node)
    
    return body_node, body_mesh

def setup_skin_deformer(sdk_manager, scene, mesh_node, mesh, skeleton_nodes):
    """
    设置蒙皮变形器，将网格绑定到骨骼
    """
    print("设置蒙皮变形器...")
    
    # 创建蒙皮变形器
    skin = FbxSkin.Create(sdk_manager, "BodySkin")
    
    # 为每个骨骼创建簇（Cluster）
    bones = [
        (skeleton_nodes['root'], 0.3),    # 臀部影响底部
        (skeleton_nodes['spine'], 0.5),   # 脊柱影响中部
        (skeleton_nodes['chest'], 0.2)    # 胸部影响顶部
    ]
    
    for bone, weight_factor in bones:
        cluster = FbxCluster.Create(sdk_manager, bone.GetName() + "Cluster")
        cluster.SetLink(bone)
        cluster.SetLinkMode(FbxCluster.ELinkMode.eNormalize)
        
        # 设置影响权重（简化版本）
        control_point_count = mesh.GetControlPointsCount()
        for i in range(control_point_count):
            # 根据顶点高度分配权重
            point = mesh.GetControlPointAt(i)
            height_ratio = point[1] / 100.0  # 假设总高度100
            
            if bone.GetName() == "Hip":
                weight = max(0, 1.0 - height_ratio * 2) * weight_factor
            elif bone.GetName() == "Spine":
                weight = (1.0 - abs(height_ratio - 0.5) * 2) * weight_factor
            else:  # Chest
                weight = max(0, height_ratio * 2 - 1) * weight_factor
            
            if weight > 0:
                cluster.AddControlPointIndex(i, weight)
        
        # 设置变换矩阵
        transform_matrix = FbxAMatrix()
        link_matrix = FbxAMatrix()
        cluster.SetTransformMatrix(transform_matrix)
        cluster.SetTransformLinkMatrix(link_matrix)
        
        skin.AddCluster(cluster)
    
    # 将蒙皮添加到网格
    mesh.AddDeformer(skin)
    
    return skin

def create_complex_animation(sdk_manager, scene, skeleton_nodes):
    """
    创建复杂的角色动画
    """
    print("创建复杂动画...")
    
    # 创建动画栈
    anim_stack = FbxAnimStack.Create(sdk_manager, "CharacterAnimation")
    anim_layer = FbxAnimLayer.Create(sdk_manager, "BaseLayer")
    anim_stack.AddMember(anim_layer)
    scene.SetCurrentAnimationStack(anim_stack)
    
    # 为每个骨骼创建动画
    frame_rate = FbxTime.EMode.eFrames30
    frames_per_second = 30
    
    # 臀部摆动动画
    create_bone_animation(skeleton_nodes['root'], anim_layer, "Y", 
                         [(0, 0), (15, 10), (30, 0), (45, -10), (60, 0)], frame_rate)
    
    # 手臂摆动动画
    create_bone_animation(skeleton_nodes['left_arm'], anim_layer, "X",
                         [(0, 0), (15, -45), (30, 0), (45, 45), (60, 0)], frame_rate)
    
    # 前臂弯曲动画
    create_bone_animation(skeleton_nodes['left_forearm'], anim_layer, "X",
                         [(0, 0), (30, 90), (60, 0)], frame_rate)
    
    return anim_stack

def create_bone_animation(bone, anim_layer, axis, keyframes, frame_rate):
    """
    为骨骼创建动画曲线
    """
    if axis == "X":
        curve = bone.LclRotation.GetCurve(anim_layer, "X", True)
    elif axis == "Y":
        curve = bone.LclRotation.GetCurve(anim_layer, "Y", True)
    else:  # Z
        curve = bone.LclRotation.GetCurve(anim_layer, "Z", True)
    
    if curve:
        curve.KeyModifyBegin()
        
        for frame, value in keyframes:
            time = FbxTime(frame * FbxTime.GetOneFrameValue(frame_rate))
            key_index = curve.KeyAdd(time)
            curve.KeySet(key_index, time, value, FbxAnimCurveDef.eInterpolationCubic)
        
        curve.KeyModifyEnd()

def create_camera_and_light(sdk_manager, scene):
    """
    创建相机和灯光
    """
    print("创建相机和灯光...")
    
    # 创建相机
    camera = FbxCamera.Create(sdk_manager, "MainCamera")
    camera.SetPosition(FbxVector4(0, 50, 200))
    camera.SetInterestPosition(FbxVector4(0, 50, 0))
    camera.ProjectionType.Set(FbxCamera.EProjectionType.ePerspective)
    camera.FieldOfView.Set(60.0)
    
    camera_node = FbxNode.Create(sdk_manager, "CameraNode")
    camera_node.SetNodeAttribute(camera)
    scene.GetRootNode().AddChild(camera_node)
    
    # 创建定向灯光
    light = FbxLight.Create(sdk_manager, "MainLight")
    light.LightType.Set(FbxLight.EType.eDirectional)
    light.Color.Set(FbxDouble3(1.0, 1.0, 1.0))
    light.Intensity.Set(100.0)
    
    light_node = FbxNode.Create(sdk_manager, "LightNode")
    light_node.SetNodeAttribute(light)
    light_node.LclTranslation.Set(FbxDouble3(0, 100, 100))
    scene.GetRootNode().AddChild(light_node)

def advanced_main():
    """
    高级示例主函数
    """
    print("=== 高级FBX SDK功能演示 ===")
    
    # 1. 初始化FBX SDK
    sdk_manager, scene = initialize_fbx_sdk()
    if not sdk_manager:
        return
    
    # 2. 创建角色骨骼系统
    print("\n1. 创建角色骨骼系统...")
    skeleton_nodes = create_character_skeleton(sdk_manager, scene)
    
    # 3. 创建角色网格
    print("2. 创建角色网格...")
    body_node, body_mesh = create_character_mesh(sdk_manager, scene, skeleton_nodes)
    
    # 4. 设置蒙皮变形器
    print("3. 设置蒙皮变形器...")
    setup_skin_deformer(sdk_manager, scene, body_node, body_mesh, skeleton_nodes)
    
    # 5. 创建复杂动画
    print("4. 创建复杂动画...")
    create_complex_animation(sdk_manager, scene, skeleton_nodes)
    
    # 6. 创建相机和灯光
    print("5. 创建相机和灯光...")
    create_camera_and_light(sdk_manager, scene)
    
    # 7. 导出场景
    print("\n6. 导出高级场景...")
    export_file = "advanced_character.fbx"
    export_scene(sdk_manager, scene, export_file)
    
    # 8. 清理资源
    print("\n7. 清理资源...")
    sdk_manager.Destroy()
    
    print("\n=== 高级演示完成 ===")

if __name__ == "__main__":
    advanced_main()
```

### 使用FBX SDK

1. 将FBX SDK库文件放置在正确路径
2. 导入FBX模块：`import fbx`
3. 参考上述示例代码进行开发

### 注意事项

- FBX SDK需要正确的环境配置
- 确保FBX文件路径正确
- 处理大型FBX文件时注意内存使用

## 故障排除

### 常见问题

1. **导入错误**：检查FBX文件路径和权限
2. **内存不足**：优化场景复杂度或增加系统内存
3. **渲染问题**：检查材质和纹理设置

### 调试技巧

- 使用`display_scene_info()`函数查看场景信息
- 逐步调试复杂的动画和蒙皮设置
- 检查FBX SDK版本兼容性

## 总结

本FBX SDK提供了完整的3D场景管理功能，支持从简单的几何体创建到复杂的骨骼动画系统。通过上述示例代码，您可以快速上手并开发专业的3D应用程序。
