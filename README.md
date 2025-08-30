Root Level Folders
services/
The core microservices directory containing all backend services. Each service is a standalone FastAPI application.

services/user_service/
Purpose: Manages authentication, user profiles, and RBAC
Contains:
User registration and login logic
JWT token generation and validation
Password hashing with bcrypt
User profile CRUD operations
Role and permission management
OAuth2 implementation
services/gamification_service/
Purpose: Event-driven gamification engine
Contains:
Achievement definitions and tracking
Point calculation and award logic
Leaderboard generation and caching
Kafka consumers for game events
Badge assignment logic
User statistics aggregation
services/knowledge_hub_service/
Purpose: Central content repository with dual-database strategy
Contains:
Question bank management (CRUD)
Article storage and retrieval
Topic hierarchy management
Tag system implementation
PostgreSQL integration for metadata
Weaviate integration for semantic search
Content import/export functionality
services/battle_room_service/
Purpose: Real-time multiplayer quiz management
Contains:
WebSocket connection management
Room creation and player matching
Game state synchronization via Redis Pub/Sub
Question delivery and timing logic
Score calculation and broadcasting
Real-time event handling
services/analytics_service/
Purpose: Data pipeline and metrics processing
Contains:
Kafka event consumers
TimescaleDB integration for time-series data
Performance metric calculations
User progress tracking
Scheduled aggregation jobs
Dashboard data APIs
services/ai_question_gen_service/
Purpose: AI-powered question generation
Contains:
vLLM client for model inference
Prompt engineering templates
Question validation logic
Caching strategy for generated questions
Difficulty calibration
Topic-specific generation rules
services/ai_assistant_service/
Purpose: RAG-based learning assistant
Contains:
Chat interface endpoints
Weaviate retrieval implementation
Context augmentation logic
LLM integration for response generation
Conversation history management
WebSocket support for streaming responses
services/contributor_service/
Purpose: Community content submission workflow
Contains:
Submission intake APIs
Peer review workflow engine
Approval/rejection logic
Event publishing for approved content
Contributor reputation tracking
Content quality validation
services/dashboard_service/
Purpose: Backend-for-Frontend aggregation service
Contains:
Composite API endpoints
Cross-service data aggregation
Recommendation engine
Performance summary generation
Smart reminder scheduling
Personalization logic
services/shared/
Purpose: Common utilities used across services
Contains:
Database connection pooling (database.py)
Kafka producer/consumer factories (kafka_client.py)
Redis connection management (redis_client.py)
Weaviate client wrapper (weaviate_client.py)
Common authentication utilities
Shared data models and schemas
aptiverse-frontend/
The Next.js 14 frontend application.

aptiverse-frontend/src/app/
Purpose: Next.js App Router pages and layouts
Contains:
(auth)/: Authentication pages (login, register)
dashboard/: User dashboard with stats and charts
battle-rooms/: Real-time quiz interface
knowledge-hub/: Content browsing and search
ai-assistant/: Chat interface for AI tutor
leaderboard/: Global and topic-specific rankings
Page-specific components and layouts
aptiverse-frontend/src/components/
Purpose: Reusable React components
Contains:
ui/: Base components (Button, Card, Input, Modal)
layout/: App structure (Header, Sidebar, Footer)
shared/: Common components (LoadingSpinner, ErrorBoundary)
aptiverse-frontend/src/lib/
Purpose: Frontend utilities and integrations
Contains:
api/: API client and service methods
hooks/: Custom React hooks (useAuth, useWebSocket)
utils/: Helper functions and constants
websocket/: Socket.io client implementations
aptiverse-frontend/src/store/
Purpose: Zustand state management
Contains:
authStore.ts: Authentication state
userStore.ts: User preferences and data
gameStore.ts: Battle room state
ml_ops/
Machine learning operations and model management.

ml_ops/training/
Purpose: Model training pipelines
Contains:
Fine-tuning scripts for LLMs
Data preparation utilities
Training configuration files
Evaluation metrics calculation
Dataset versioning logic
ml_ops/models/
Purpose: Model artifact storage
Contains:
Trained model checkpoints
Model configuration files
Version tracking
Performance benchmarks
ml_ops/experiments/
Purpose: MLflow experiment tracking
Contains:
Experiment logs
Hyperparameter configurations
Training metrics
Model comparison results
ml_ops/deployment/
Purpose: Model serving infrastructure
Contains:
vLLM deployment configurations
Model serving endpoints
A/B testing setup
Rollback procedures
scripts/
Purpose: Automation and setup scripts
Contains:
setup.sh: One-click development environment setup
init-db.sql: Database schema initialization
dev-tools.sh: Developer utility commands
Migration scripts
Data seeding scripts
requirements/
Purpose: Python dependency management
Contains:
base.txt: Core dependencies for all services
dev.txt: Development tools (pytest, black, mypy)
prod.txt: Production-specific dependencies
infrastructure/
Purpose: Deployment and monitoring configurations
infrastructure/kubernetes/
Contains:
Service definitions
Deployment manifests
ConfigMaps and Secrets
Ingress rules
Horizontal Pod Autoscalers
infrastructure/monitoring/
Contains:
Prometheus configuration and alerts
Grafana dashboards
Log aggregation setup
Service mesh configuration
docs/
Purpose: Project documentation
Contains:
api/: OpenAPI specifications
architecture/: System design documents, ADRs
deployment/: Production deployment guides
development/: Developer onboarding, coding standards
Root Files
docker-compose.yml
Purpose: Production-like local development environment
Contains: Service definitions for all microservices and infrastructure
docker-compose.dev.yml
Purpose: Development overrides
Contains: Volume mounts, debug ports, hot-reload configurations
docker-compose.test.yml
Purpose: Testing environment
Contains: Test database, isolated networks, CI configurations
.env.example
Purpose: Template for environment variables
Contains: All required configuration keys with example values
Makefile
Purpose: Common development commands
Contains:
make dev: Start development environment
make test: Run all tests
make build: Build all services
make migrate: Run database migrations