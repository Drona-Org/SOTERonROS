cmake_minimum_required (VERSION 3.1)
project (SOTERonROS)
set(projectName SOTERTest)
find_package (Threads)
include_directories(
    ${CMAKE_SOURCE_DIR}/../../../../../sumukh/Documents/P/Bld/Drops/Prt/include
    ${CMAKE_SOURCE_DIR}/SOTERonROS/Src/Lib/ExternalMotionPlanners/OMPLOptimalPlanner/Includes
    ${CMAKE_SOURCE_DIR}/SOTERonROS/Src/Lib/WorkspaceRelated/WorkspaceParser/Includes)

add_executable(robot_test
    Applications/RobotSurveillance/MainRobotSurveillanceTaskPlanner.h
    Applications/RobotSurveillance/MainRobotSurveillanceTaskPlanner.c
    Applications/RobotSurveillance/Main.cpp
    RobotSDK/RobotFuncs.h
    RobotSDK/RobotFuncs.cpp
    Applications/RobotSurveillance/Exp1.xml
    ${CMAKE_SOURCE_DIR}/SOTERonROS/Src/Lib/WorkspaceRelated/WorkspaceParser/Includes/Workspace.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/Src/Lib/WorkspaceRelated/WorkspaceParser/Includes/tinyxml2.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/Src/Lib/WorkspaceRelated/WorkspaceParser/Includes/WorkspaceParser.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/include/ext_compat.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/include/libhandler.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/include/libhandler-internal.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/include/Prt.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/include/PrtConfig.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/include/PrtExecution.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/include/PrtLinuxUserConfig.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/include/PrtProgram.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/include/PrtTypes.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/include/PrtValues.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/include/sal.h)

add_executable(soter_test
    Applications/DroneExploration/MainDroneTaskPlanner.h
    Applications/DroneExploration/MainDroneTaskPlanner.c
    Applications/DroneExploration/Main.cpp
    Applications/DroneExploration/Exp2.xml
    RobotSDK/RobotFuncsDrone.h
    RobotSDK/RobotFuncsDrone.cpp
    ${CMAKE_SOURCE_DIR}/SOTERonROS/Src/Lib/WorkspaceRelated/WorkspaceParser/Includes/Workspace.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/Src/Lib/WorkspaceRelated/WorkspaceParser/Includes/tinyxml2.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/Src/Lib/WorkspaceRelated/WorkspaceParser/Includes/WorkspaceParser.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/include/ext_compat.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/include/libhandler.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/include/libhandler-internal.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/include/Prt.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/include/PrtConfig.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/include/PrtExecution.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/include/PrtLinuxUserConfig.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/include/PrtProgram.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/include/PrtTypes.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/include/PrtValues.h
    ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/include/sal.h)

    target_link_libraries(soter_test ${OMPL_LIBRARIES} ${OMPLAPP_LIBRARIES} ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/lib/libPrt_static.a ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Ext/libhandler/out/gcc-amd64-linux-gnu/debug/libhandler.a ${CMAKE_THREAD_LIBS_INIT} ${CMAKE_SOURCE_DIR}/SOTERonROS/Src/Lib/ExternalMotionPlanners/OMPLOptimalPlanner/libomplplanner.so ${CMAKE_SOURCE_DIR}/SOTERonROS/Src/Lib/ExternalMotionPlanners/OMPLOptimalPlanner/libomplplanner.a ${CMAKE_SOURCE_DIR}/SOTERonROS/Src/Lib/WorkspaceRelated/WorkspaceParser/libworkspaceparser.a)
    target_link_libraries(robot_test ${OMPL_LIBRARIES} ${OMPLAPP_LIBRARIES} ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Bld/Drops/Prt/lib/libPrt_static.a ${CMAKE_SOURCE_DIR}/SOTERonROS/P/Ext/libhandler/out/gcc-amd64-linux-gnu/debug/libhandler.a ${CMAKE_THREAD_LIBS_INIT} ${CMAKE_SOURCE_DIR}/SOTERonROS/Src/Lib/ExternalMotionPlanners/OMPLOptimalPlanner/libomplplanner.so ${CMAKE_SOURCE_DIR}/SOTERonROS/Src/Lib/ExternalMotionPlanners/OMPLOptimalPlanner/libomplplanner.a ${CMAKE_SOURCE_DIR}/SOTERonROS/Src/Lib/WorkspaceRelated/WorkspaceParser/libworkspaceparser.a)
